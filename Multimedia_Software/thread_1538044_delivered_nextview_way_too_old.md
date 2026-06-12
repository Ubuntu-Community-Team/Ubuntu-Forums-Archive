---
title: "delivered nextview way too old"
date: 2010-07-24
forum: Multimedia Software
---

### Post by Mr.Gosh on 2010-07-24
Hello Guys,

I give ubuntu or exactly mythtbuntu 10.04 another try.
the last thing that doesnt work is the epg grabbing with [Nextview]("http://nxtvepg.sf.net") but thats logical how I found out now!

The shipped version from ubuntu is 2.7.6 - well and that one just worked for kernel 2.6.16 - since than is nextview 2.8.0 needed in cause of the changed kernel drivers!

so there are no .deb 64 bit packes of nextview 2.8.0 or 2.8.1 around in the web! :(

I tried to compile it myself - but that doesn work either, possibly you can help me with that:

the output from ```
make all
``` posts the following:
```
make all
gcc -pipe -g -O2 -Wall -Wnested-externs -Wstrict-prototypes -Wmissing-prototypes -Wno-pointer-sign -I. -I/usr/X11R6/include -Ibuild-x86_64 -DX11_APP_DEFAULTS=\"/etc/X11/app-defaults/Nxtvepg\" -DTK_LIBRARY_PATH=\"/usr/lib/tk8.4\" -DTCL_LIBRARY_PATH=\"/usr/lib/tcl8.4\" -DUSE_THREADS -DUSE_XMLTV_IMPORT -DUSE_TTX_GRABBER -DUSE_DAEMON -DEPG_DB_DIR=\"/var/tmp/nxtvdb\" -Wp,-MMD,build-x86_64/epgui/pibox.o.dep.tmp -c -o build-x86_64/epgui/pibox.o epgui/pibox.c
epgui/pibox.c:35:17: warning: tcl.h: No such file or directory
epgui/pibox.c:36:16: warning: tk.h: No such file or directory
In file included from epgui/pibox.c:43:
./epgui/pioutput.h:60: error: expected specifier-qualifier-list before &#8216;Tcl_Obj&#8217;
epgui/pibox.c:193: error: expected &#8216;)&#8217; before &#8216;ttp&#8217;
epgui/pibox.c: In function &#8216;PiBox_Create&#8217;:
epgui/pibox.c:246: warning: implicit declaration of function &#8216;Tcl_CreateObjCommand&#8217;
epgui/pibox.c:246: warning: nested extern declaration of &#8216;Tcl_CreateObjCommand&#8217;
epgui/pibox.c:246: error: &#8216;interp&#8217; undeclared (first use in this function)
epgui/pibox.c:246: error: (Each undeclared identifier is reported only once
epgui/pibox.c:246: error: for each function it appears in.)
epgui/pibox.c:246: error: &#8216;PiBox_Toggle&#8217; undeclared (first use in this function)
epgui/pibox.c:251: warning: implicit declaration of function &#8216;PiBox_Toggle&#8217;
make: *** [build-x86_64/epgui/pibox.o] Error 1
```and so essential parts are not compiled.
that leeds to the follwing error during ```
sudo make install
``````
sudo make install
test -d /usr/local/bin || install -d /usr/local/bin
test -d /usr/local/man/man1 || install -d /usr/local/man/man1
test -d /etc/X11/app-defaults || install -d /etc/X11/app-defaults
test -d /var/tmp/nxtvdb || install -d /var/tmp/nxtvdb
chmod 0777 /var/tmp/nxtvdb
install -c -m 0755 build-x86_64/nxtvepg /usr/local/bin
install: cannot stat `build-x86_64/nxtvepg': No such file or directory
make: *** [install] Error 1
```funny enough that no one recognizes that the shipped version CAN'T work - also the compile doesnt work and I cannot find a precompiled .dep package for 64 bit.?!? 

:( PLEASE HELP

---

### Post by kwbolte on 2010-07-25
Okay, this is how I tried it:


[LIST=1]
[*]change paths in Makefile:
```
prefix  = /usr
mandir  = $(ROOT)/usr/share/man/man1
bTK_LIBRARY_PATH  = /usr/share/tcltk/tk$(TCL_VER)
TCL_LIBRARY_PATH = /usr/share/tcltk/tcl$(TCL_VER)
```
[*]install packages:
flex, byacc-j, tclx8.4, tcl8.4-dev, tk8.4-dev, libx11-dev, libxmu6, libxmu-dev
[/LIST]
Which gave this error:

 is not a valid Tcl/Tk library directory
Check the definitions of TCL_LIBRARY_PATH and TK_LIBRARY_PATH

For me [FONT=Courier New]/usr/share/tcltk[/FONT] looks like the right place, anybody an idea about this?
@Mr.Gosh: Could you try to compile with this? Do a make clean first.

---

### Post by kwbolte on 2010-07-26
Okay, this type caused the error:  > **kwbolte said:**
>  **b**TK_LIBRARY_PATH  = /usr/share/tcltk/tk$(TCL_VER)   
This line has to be
[FONT=Courier New]TK_LIBRARY_PATH  = /usr/share/tcltk/tk$(TCL_VER)[/FONT]  

Additional I compiled it with TCL/TK 8.5 as suggested by the README. 
Therefor you need packages:
 tcl8.5 , tcl8.5-dev , tcl8.5-kwwidges , tk8.5 , tk8.5-dev
and change the lines with [FONT=Courier New]TCL_VER[/FONT] in Makefile as follows: 
[FONT=Courier New]#TCL_VER := $(shell echo 'puts [package require Tcl]' | tclsh) 
TCL_VER = 8.5[/FONT]

After all I did  make make all sudo make install  and it works!  Additional info is in the (german) wiki: [http://wiki.ubuntuusers.de/nxtvepg](http://wiki.ubuntuusers.de/nxtvepg)

So my Makefile looks like this (until "don't change anything below"):

```

ifeq ($(OS),Windows_NT)
# for Windows a separate makefile is used
include Makefile.win32
else
OS = $(shell uname)
ifeq ($(OS), FreeBSD)
include Makefile.bsd
else
ifeq ($(OS), NetBSD)
include Makefile.bsd
else

ROOT    =
prefix  = /usr
exec_prefix = ${prefix}
bindir  = $(ROOT)${exec_prefix}/bin
mandir  = $(ROOT)/usr/share/man/man1
resdir  = $(ROOT)/etc/X11
cfgdir  = $(ROOT)/usr/share/nxtvepg

# if you have perl and/or flex set their path here, else just leave them alone
PERL    = /usr/bin/perl
FLEX    = /usr/bin/flex
YACC    = /usr/bin/yacc

# select Tcl/Tk version (8.5 recommended due to modernized widget appearence)
#TCL_VER := $(shell echo 'puts [package require Tcl]' | tclsh)
TCL_VER = 8.5

ifeq ($(shell test -d /usr/include/tcl$(TCL_VER) && echo YES),YES)
INCS   += -I/usr/include/tcl$(TCL_VER)
endif

GUILIBS  = -ltk$(TCL_VER) -ltcl$(TCL_VER) -L/usr/X11R6/lib -lX11 -lXmu -ldl

# use static libraries for debugging only
#GUILIBS += -Ldbglib -static

INCS   += -I. -I/usr/X11R6/include
DEFS   += -DX11_APP_DEFAULTS=\"$(resdir)/app-defaults/Nxtvepg\"
# path to Tcl/Tk headers, if not properly installed
#INCS   += -I/usr/local/tcl/tcl8.0/generic -I/usr/local/tcl/tk8.0/generic

# path to Tcl/Tk script library (note Tk is sometimes in X11/lib/tk#.#)
bTK_LIBRARY_PATH  = /usr/share/tcltk/tk$(TCL_VER)
TK_LIBRARY_PATH  = /usr/share/tcltk/tk$(TCL_VER)
TCL_LIBRARY_PATH = /usr/share/tcltk/tcl$(TCL_VER)
DEFS   += -DTK_LIBRARY_PATH=\"$(TK_LIBRARY_PATH)\"
DEFS   += -DTCL_LIBRARY_PATH=\"$(TCL_LIBRARY_PATH)\"

# enable use of multi-threading
DEFS    += -DUSE_THREADS
ACQLIBS += -lpthread

# use UTF-8 internally instead of Latin-1 (EXPERIMENTAL)
#DEFS   += -DUSE_UTF8 -DXMLTV_OUTPUT_UTF8

# enable support for importing XMLTV files
DEFS   += -DUSE_XMLTV_IMPORT -DXMLTV_CNI_MAP_PATH=\"$(cfgdir)\"

# enable support for teletext EPG grabber (EXPERIMENTAL)
# external grabber script is searched for in $PATH (unless you define an absolute path)
DEFS   += -DUSE_TTX_GRABBER -DTTX_GRAB_SCRIPT_PATH=\"$(cfgdir)\"

# enable use of daemon and client/server connection
DEFS   += -DUSE_DAEMON

# enable if you have both 32-bit and 64-bit systems
#DEFS   += -DUSE_32BIT_COMPAT

# specify path to header file for video4linux device driver (default: use internal copy)
#DEFS  += -DPATH_VIDEODEV_H=\"/usr/include/linux/videodev.h\"

# enable use of libzvbi
# (automatically uses the VBI proxy, if the daemon is running)
#DEFS   += -DUSE_LIBZVBI
#ACQLIBS += -lzvbi -lpthread -lpng

# The database directory can be either in the user's $HOME (or relative to any
# other env variable) or at a global place like /var/spool (world-writable)
# -> uncomment 2 lines below to put the databases in the user's home
#USER_DBDIR  = .nxtvdb
#DEFS       += -DEPG_DB_ENV=\"HOME\" -DEPG_DB_DIR=\"$(USER_DBDIR)\"
ifndef USER_DBDIR
SYS_DBDIR    = /var/tmp/nxtvdb
DEFS        += -DEPG_DB_DIR=\"$(SYS_DBDIR)\"
INST_DB_DIR  = $(ROOT)$(SYS_DBDIR)
INST_DB_PERM = 0777
endif

WARN    = -Wall -Wnested-externs -Wstrict-prototypes -Wmissing-prototypes
WARN   += -Wno-pointer-sign
#WARN  += -Wcast-align -Wpointer-arith -Werror
#WARN  += -Wcast-qual -Wwrite-strings -Wshadow
CC      = gcc
# the following flags can be overridden by an environment variable with the same name
CFLAGS ?= -pipe -g -O2
CFLAGS += $(WARN) $(INCS) $(DEFS)
LDFLAGS += -lm
#CFLAGS += -ftest-coverage -fprofile-arcs
#LDFLAGS += -ftest-coverage -fprofile-arcs
#LDFLAGS += -pg

BUILD_DIR  = build-$(shell uname -m | sed -e 's/i.86/i386/' -e 's/ppc/powerpc/')
INCS      += -I$(BUILD_DIR)

# FIXME required for O2
$(BUILD_DIR)/epgui/rcfile.o : CFLAGS += -fno-strict-aliasing

# end Linux specific part
endif
endif

# ----- don't change anything below ------------------------------------------


```

---

### Post by Mr.Gosh on 2010-07-29
Perfect!!!!

Thanks - that worked!
Now Nextview recognizes all my bttv cards out of the box!
How can I create a .deb file out of this? For other Nextview users who wanna give ubuntu a try?

Greetings - Mr.Gosh :popcorn:

---

### Post by Mr.Gosh on 2010-08-08
Well - no easy discription anyone - how to build a .deb file of a compile?

---

