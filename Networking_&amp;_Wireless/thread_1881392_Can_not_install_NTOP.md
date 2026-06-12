---
title: "Can not install NTOP"
date: 2011-11-15
forum: Networking &amp; Wireless
---

### Post by hamena314 on 2011-11-15
Hi,

I'm trying to install NTOP 4.1.1 on Ubuntu 10.04. Checked it our of the SVN and did

```

sudo ./autogen.sh
sudo make

```

without any error. But "make install" gives this:

```
deepblue1@deepblue1-desktop:/ntop$ sudo make install
Making install in .
make[1]: Betrete Verzeichnis '/ntop'
make[2]: Betrete Verzeichnis '/ntop'
test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"
/bin/bash ./libtool --mode=install /usr/bin/install -c libntop.la libntopreport.la '/usr/local/lib'
libtool: install: /usr/bin/install -c .libs/libntop-4.1.1.so /usr/local/lib/libntop-4.1.1.so
libtool: install: (cd /usr/local/lib && { ln -s -f libntop-4.1.1.so libntop.so || { rm -f libntop.so && ln -s libntop-4.1.1.so libntop.so; }; })
libtool: install: /usr/bin/install -c .libs/libntop.lai /usr/local/lib/libntop.la
libtool: install: warning: relinking `libntopreport.la'
libtool: install: (cd /ntop; /bin/bash /ntop/libtool --tag CC --mode=relink gcc -g -O2 -I/usr/local/include -I/opt/local/include -Wshadow -Wpointer-arith -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -fPIC -DPIC -I/usr/include/python2.6 -I/usr/include/python2.6 -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -release 4.1.1 -export-dynamic -L/usr/local/lib -L/opt/local/lib -o libntopreport.la -rpath /usr/local/lib emitter.lo globals-report.lo graph.lo http.lo report.lo reportUtils.lo ssl.lo webInterface.lo map.lo python.lo libntop.la -lcrypt -lc -lssl -lcrypto -lrrd_th -lgdbm -lz -lpthread -ldl -lutil -lm -lpython2.6 -lGeoIP -lpcap ./opendpi-ntop/src/lib/.libs/libopendpi.a )

*** Warning: Linking the shared library libntopreport.la against the
*** static library ./opendpi-ntop/src/lib/.libs/libopendpi.a is not portable!
libtool: relink: gcc -shared .libs/emitter.o .libs/globals-report.o .libs/graph.o .libs/http.o .libs/report.o .libs/reportUtils.o .libs/ssl.o .libs/webInterface.o .libs/map.o .libs/python.o -L/usr/local/lib -L/opt/local/lib -lntop -lcrypt -lc -lssl -lcrypto -L/usr/lib -lrrd_th -lgdbm -lz -lpthread -ldl -lutil -lm -lpython2.6 -lGeoIP -lpcap ./opendpi-ntop/src/lib/.libs/libopendpi.a -pthread -Wl,-soname -Wl,libntopreport-4.1.1.so -o .libs/libntopreport-4.1.1.so
libtool: install: /usr/bin/install -c .libs/libntopreport-4.1.1.soT /usr/local/lib/libntopreport-4.1.1.so
libtool: install: (cd /usr/local/lib && { ln -s -f libntopreport-4.1.1.so libntopreport.so || { rm -f libntopreport.so && ln -s libntopreport-4.1.1.so libntopreport.so; }; })
libtool: install: /usr/bin/install -c .libs/libntopreport.lai /usr/local/lib/libntopreport.la
libtool: install: /usr/bin/install -c .libs/libntop.a /usr/local/lib/libntop.a
libtool: install: chmod 644 /usr/local/lib/libntop.a
libtool: install: ranlib /usr/local/lib/libntop.a
libtool: install: /usr/bin/install -c .libs/libntopreport.a /usr/local/lib/libntopreport.a
libtool: install: chmod 644 /usr/local/lib/libntopreport.a
libtool: install: ranlib /usr/local/lib/libntopreport.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
/usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
- add LIBDIR to the `LD_LIBRARY_PATH' environment variable
during execution
- add LIBDIR to the `LD_RUN_PATH' environment variable
during linking
- use the `-Wl,-rpath -Wl,LIBDIR' linker flag
- have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
/bin/bash ./libtool --mode=install /usr/bin/install -c ntop '/usr/local/bin'
libtool: install: /usr/bin/install -c .libs/ntop /usr/local/bin/ntop
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
cp: Aufruf von stat fÃ¼r â€žhtml/PlotKitâ€œ nicht mÃ¶glich: Datei oder Verzeichnis nicht gefunden
cp: Aufruf von stat fÃ¼r â€žhtml/PlotKit/*jsâ€œ nicht mÃ¶glich: Datei oder Verzeichnis nicht gefunden
cp: Aufruf von stat fÃ¼r â€žhtml/MochiKitâ€œ nicht mÃ¶glich: Datei oder Verzeichnis nicht gefunden
cp: Aufruf von stat fÃ¼r â€žhtml/MochiKit/*jsâ€œ nicht mÃ¶glich: Datei oder Verzeichnis nicht gefunden
cp: Aufruf von stat fÃ¼r â€žhtml/PlotKitâ€œ nicht mÃ¶glich: Datei oder Verzeichnis nicht gefunden
cp: Aufruf von stat fÃ¼r â€žhtml/PlotKit/*.jsâ€œ nicht mÃ¶glich: Datei oder Verzeichnis nicht gefunden
cp: Aufruf von stat fÃ¼r â€žhtml/MochiKitâ€œ nicht mÃ¶glich: Datei oder Verzeichnis nicht gefunden
cp: Aufruf von stat fÃ¼r â€žhtml/MochiKit/*.jsâ€œ nicht mÃ¶glich: Datei oder Verzeichnis nicht gefunden
make[2]: *** [install-data-local] Fehler 1
make[2]: Verlasse Verzeichnis '/ntop'
make[1]: *** [install-am] Fehler 2
make[1]: Verlasse Verzeichnis '/ntop'
make: *** [install-recursive] Fehler 1

```

Whats not working?

HAVE PHUN!

---

### Post by WasMeHere on 2011-11-15
Hi hamena314,

Did you try ```
sudo apt-get install ntop
``` or is that version to old for your purpose?

Have phun finding out about Ubuntu :-)
Olle

---

