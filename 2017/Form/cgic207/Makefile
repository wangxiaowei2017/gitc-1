CFLAGS=-g -Wall
CC=gcc
AR=ar
RANLIB=ranlib
LIBS= -lsqlite3 -L./ -lcgic

all: libcgic.a mytest.cgi capture

install: libcgic.a
	cp libcgic.a /usr/local/lib
	cp cgic.h /usr/local/include
	@echo libcgic.a is in /usr/local/lib. cgic.h is in /usr/local/include.

libcgic.a: cgic.o cgic.h
	rm -f libcgic.a
	$(AR) rc libcgic.a cgic.o
	$(RANLIB) libcgic.a

#mingw32 and cygwin users: replace .cgi with .exe

mytest.cgi: mytest.o libcgic.a
	gcc mytest.o -o mytest.cgi ${LIBS}

capture: capture.o libcgic.a
	gcc capture.o -o capture ${LIBS}

clean:
	rm -f *.o *.a cgictest.cgi capture cgicunittest

test:
	gcc -D UNIT_TEST=1 cgic.c -o cgicunittest
	./cgicunittest
