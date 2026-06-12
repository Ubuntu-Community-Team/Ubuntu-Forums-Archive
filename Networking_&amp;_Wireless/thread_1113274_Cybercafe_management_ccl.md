---
title: "Cybercafe management ccl"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by omuony on 2009-04-01
I have installed cafe con leche CCL, on my cyber and when i try to run the server i get this error
> cclfox: error while loading shared libraries: libccls.so.0: cannot open shared object file: No such file or directory

This is the install feedback
> user1@computer1:~/libccls-0.7.0$ sudo make install
Making install in src
make[1]: Entering directory `/home/user1/libccls-0.7.0/src'
make[2]: Entering directory `/home/user1/libccls-0.7.0/src'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libccls.la' '/usr/local/lib/libccls.la'
/usr/bin/install -c .libs/libccls.so.0.7.0 /usr/local/lib/libccls.so.0.7.0
(cd /usr/local/lib && rm -f libccls.so.0 && ln -s libccls.so.0.7.0 libccls.so.0)
(cd /usr/local/lib && rm -f libccls.so && ln -s libccls.so.0.7.0 libccls.so)
/usr/bin/install -c .libs/libccls.lai /usr/local/lib/libccls.la
/usr/bin/install -c .libs/libccls.a /usr/local/lib/libccls.a
ranlib /usr/local/lib/libccls.a
chmod 644 /usr/local/lib/libccls.a
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib


Please help. I  would like to run my cybercafe on completely open source software.

---

