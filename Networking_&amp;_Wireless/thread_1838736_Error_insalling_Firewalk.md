---
title: "Error insalling Firewalk"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by atulsingh7890 on 2011-09-04
I was installing firewal-0.99.1 when i ran configure script it gives
#./configure
loading cache ./config.cache
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking build system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc -O3 -funroll-loops -fomit-frame-pointer -pipe ) works... yes
checking whether the C compiler (gcc -O3 -funroll-loops -fomit-frame-pointer -pipe ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking for libnet_build_ip in -lnet... (cached) no



when i have done search of libnet
it gives
#whereis libnet
libnet: /usr/lib/libnet.la /usr/lib/libnet.a /usr/lib/libnet.so /usr/include/libnet /usr/include/libnet.h /usr/man/man3/libnet.3

do guide me friends........

---

### Post by gmargo on 2011-09-04
Please provide better information.  Where did this "firewalk" source come from?

Google is not making it obvious.  I see this version 5.0 at [http://packetfactory.openwall.net/projects/firewalk/](http://packetfactory.openwall.net/projects/firewalk/)

---

### Post by atulsingh7890 on 2011-09-04
I got it from 
this link...
[http://packetstormsecurity.org/files/10767/firewalk-0.99.1.tar.gz.html](http://packetstormsecurity.org/files/10767/firewalk-0.99.1.tar.gz.html)

---

### Post by gmargo on 2011-09-05
That 0.99 version is very old - 1999 vintage.  The 5.0 version is 2002 vintage, so a bit more current.  I'd try that one instead.   

Also, regarding the libnet question - youl need to install the **libnet1-dev** package.

---

### Post by atulsingh7890 on 2011-09-10
thanks for the help ..
i have been tried installing version 5.0 and libnet1-dev is also installed
But it now gives the configure error as
./configure
beginning autoconfiguration process for firewalk-5.0...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking for libnet_build_ipv4 in -lnet... yes
checking for pcap_open_live in -lpcap... yes
checking for arp_get in -ldnet... no
configure: error: No libdnet?  [http://libdnet.sourceforge.net](http://libdnet.sourceforge.net).
root@ATul:/home/atul/Downloads/Firewalk# 


I have tried making all the symbolic lynks to libdnet as follows...

# cd /usr/lib
# ln -s /usr/local/lib/libdnet.a libdnet.a
# cd /usr/include
# ln -s /usr/local/include/dnet.h dnet.h
# ln -s /usr/local/include/dnet/ dnet

BUt nothing happened...it is still giving that configure error...Please help me..

---

### Post by atulsingh7890 on 2011-09-10
thanks for the help ..
i have been tried installing version 5.0 and libnet1-dev is also installed
But it now gives the configure error as
./configure
beginning autoconfiguration process for firewalk-5.0...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking for libnet_build_ipv4 in -lnet... yes
checking for pcap_open_live in -lpcap... yes
checking for arp_get in -ldnet... no
configure: error: No libdnet?  [http://libdnet.sourceforge.net](http://libdnet.sourceforge.net).
root@ATul:/home/atul/Downloads/Firewalk# 


I have tried making all the symbolic lynks to libdnet as follows...

# cd /usr/lib
# ln -s /usr/local/lib/libdnet.a libdnet.a
# cd /usr/include
# ln -s /usr/local/include/dnet.h dnet.h
# ln -s /usr/local/include/dnet/ dnet

BUt nothing happened...it is still giving that configure error...Please help me..

---

### Post by gmargo on 2011-09-10
It would appear, in Debian and Ubuntu distributions, that the **libdnet** you are looking for, is actually called **libdumbnet** due to a name conflict with a DECnet library.

So, you will need to install the **libdumbnet1** and **libdumbnet-dev** packages, and then edit the "configure" file to use "-ldumbnet" instead of "-ldnet".  Also edit include/firewalk.h to #include dumbnet.h instead of dnet.h.  (I've no idea why your own compiled version didn't work.)

Exactly what OS version are you compiling on?  I tried on 64-bit Maverick and the configure failed immediately trying to determine system type; I think it needs an updated config.guess.

Update: It compiled on 32-bit Maverick.  Had to add a "break" after a "default:" in a switch statement in firewalk.c.

---

### Post by atulsingh7890 on 2011-09-11
Thanks for the above help....

by replacing the name of the ldnet to dumbnet ....
configure ran succesfully...
I am compiling this source in Lucid Lynx ,

Here is the configure output...

./configure
beginning autoconfiguration process for firewalk-5.0...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for executable suffix... 
checking for object suffix... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking for libnet_build_ipv4 in -lnet... yes
checking for pcap_open_live in -lpcap... yes
checking for arp_get in -ldnet... yes
checking for ANSI C header files... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for strerror... yes
checking for bpf... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating version.h
config.status: creating include/config.h

**When i have done make**

root@ATul:/home/atul/Downloads/Firewalk# make
Making all in src
make[1]: Entering directory `/home/atul/Downloads/Firewalk/src'
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c init.c
init.c: In function &#8216;fw_init_net&#8217;:
init.c:92: warning: assignment discards qualifiers from pointer target type
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c firewalk.c
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c main.c
main.c: In function &#8216;main&#8217;:
main.c:78: warning: pointer targets in passing argument 1 of &#8216;usage&#8217; differ in signedness
../include/firewalk.h:282: note: expected &#8216;u_char *&#8217; but argument is of type &#8216;char *&#8217;
main.c:125: warning: pointer targets in passing argument 1 of &#8216;usage&#8217; differ in signedness
../include/firewalk.h:282: note: expected &#8216;u_char *&#8217; but argument is of type &#8216;char *&#8217;
main.c:136: warning: pointer targets in passing argument 1 of &#8216;usage&#8217; differ in signedness
../include/firewalk.h:282: note: expected &#8216;u_char *&#8217; but argument is of type &#8216;char *&#8217;
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c packet_build.c
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c packet_capture.c
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c packet_filter.c
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c packet_inject.c
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c packet_update.c
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c packet_verify.c
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c report.c
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c signal.c
gcc -DHAVE_CONFIG_H -I. -I. -I../include     -g -O2 -Wall -c util.c
gcc  -g -O2 -Wall  -o firewalk  init.o firewalk.o main.o packet_build.o packet_capture.o packet_filter.o packet_inject.o packet_update.o packet_verify.o report.o signal.o util.o  -ldnet -lpcap -lnet 
packet_build.o: In function `fw_packet_build_probe':
/home/atul/Downloads/Firewalk/src/packet_build.c:101: undefined reference to `route_open'
/home/atul/Downloads/Firewalk/src/packet_build.c:110: undefined reference to `addr_pton'
/home/atul/Downloads/Firewalk/src/packet_build.c:118: undefined reference to `route_get'
/home/atul/Downloads/Firewalk/src/packet_build.c:124: undefined reference to `route_close'
/home/atul/Downloads/Firewalk/src/packet_build.c:126: undefined reference to `arp_open'
/home/atul/Downloads/Firewalk/src/packet_build.c:134: undefined reference to `arp_get'
/home/atul/Downloads/Firewalk/src/packet_build.c:140: undefined reference to `arp_close'
/home/atul/Downloads/Firewalk/src/packet_build.c:121: undefined reference to `route_close'
/home/atul/Downloads/Firewalk/src/packet_build.c:137: undefined reference to `arp_close'
/home/atul/Downloads/Firewalk/src/packet_build.c:105: undefined reference to `route_close'
/home/atul/Downloads/Firewalk/src/packet_build.c:151: undefined reference to `arp_close'
collect2: ld returned 1 exit status
make[1]: *** [firewalk] Error 1
make[1]: Leaving directory `/home/atul/Downloads/Firewalk/src'
make: *** [all-recursive] Error 1



i have also inserted the break after default......
i m compiling on a 32-bit machine

---

### Post by gmargo on 2011-09-11
> **atulsingh7890 said:**
> 
gcc  -g -O2 -Wall  -o firewalk  init.o firewalk.o main.o packet_build.o packet_capture.o packet_filter.o packet_inject.o packet_update.o packet_verify.o report.o signal.o util.o  [COLOR=Red]-ldnet[/COLOR] -lpcap -lnet 


The are two references to "-ldnet" in the configure file, I think you missed the second one.

---

### Post by atulsingh7890 on 2011-09-11
I got that.......
it is now installed..
Thanks for your help..
:D

---

