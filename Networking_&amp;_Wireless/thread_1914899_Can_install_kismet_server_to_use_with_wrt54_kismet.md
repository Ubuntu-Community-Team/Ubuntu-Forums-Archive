---
title: "Can install kismet server to use with wrt54 kismet drone"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by rmortim on 2012-01-25
Hi
I am trying to Install a kismet drone on my wrt54gl and the server on ubuntu 11.10 using kismet-2005-06-R1.I have got the drone working and running(as seen below).

But have a issue when trying to install the server package. Not to sure if its still having a problem with configure or the make commands. I do apologise as im a noob with linux and still trying to learn my ways
```


root@DD-WRT:~# /tmp/kismet_drone
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Disabling channel hopping.
Source 0 (Kismet-Drone): Enabling monitor mode for wrt54g source interface prism0 channel 0...
Source 0 (Kismet-Drone): Opening wrt54g source interface prism0...
NOTICE: bind address not specified, using INADDR_ANY.
Kismet Drone 2005.06.R1 (Kismet)
Listening on port 3501 (protocol 9).
Allowing connections from 127.0.0.1/255.255.255.255
Allowing connections from 10.0.0.0/255.255.255.0



Below is the configure and make results from terminal




checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for platform-specific compiler flags... none needed
checking whether byte ordering is bigendian... no
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking for unistd.h... (cached) yes
checking for sys/types.h... (cached) yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for ANSI C header files... (cached) yes
checking return type of signal handlers... void
checking whether lstat dereferences a symlink specified with a trailing slash... yes
checking whether stat accepts an empty string... no
checking for gettimeofday... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strcasecmp... yes
checking for strftime... yes
checking for strstr... yes
checking for system-level getopt_long()... yes
checking for stdint.h... (cached) yes
checking for accept() addrlen type... socklen_t
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for _LARGE_FILES value needed for large files... no
checking for group 'root'... yes
checking for group 'man'... checking for initscr in -lncurses... yes
checking for new_panel in -lpanel... yes
checking for assume_default_colors in -lncurses... yes
checking for linux/netlink.h... no
configure: WARNING: *** Missing Linux netlink headers.  wlanng_legacy source will not be built. ***
checking for linux/wireless.h... no
configure: WARNING: *** Missing Linux Wireless kernel extentions.  The majority of packet sources on Linux require this support and will not work without it.  Make sure your kernel header packages are installed.  If all else fails, try the --with-linuxheaders directive. ***
checking for radiotap support... checking for setuid ... yes
checking for glib-config... no
configure: WARNING: Could not find glib-config in /usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games.  glib is required to link to wiretap.
configure: WARNING: *** Wiretap support disabled.  While Kismet will function without wiretap, it will limit the log reading and writing abilities. ***
checking for XML_GetCurrentLineNumber in -lexpat... no
configure: WARNING: *** Missing Expat XML library.  gpsmap will not be built. ***
checking gmp.h usability... no
checking gmp.h presence... no
checking for gmp.h... no
configure: WARNING: *** Missing GMP math library.  gpsmap will not be built. ***
checking for wget... yes
checking for Magick-config... no
configure: WARNING: *** Missing Magick-config (or it is not in the path).  gpsmap will not be built. ***
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking for pthread_create in -lpthread... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating scripts/kismet
config.status: creating extra/buzzme/Makefile
config.status: creating extra/Makefile
config.status: creating conf/kismet.conf
config.status: creating conf/kismet_ui.conf
config.status: creating config.h
configure: configuring in libpcap-0.9.1-kis
configure: running /bin/bash './configure' --prefix=/usr/local  --cache-file=/dev/null --srcdir=.
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking gcc version... 4
checking for inline... inline
checking for __attribute__... no
checking for u_int8_t using gcc... yes
checking for u_int16_t using gcc... yes
checking for u_int32_t using gcc... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking sys/ioccom.h usability... no
checking sys/ioccom.h presence... no
checking for sys/ioccom.h... no
checking sys/sockio.h usability... no
checking sys/sockio.h presence... no
checking for sys/sockio.h... no
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking for netinet/if_ether.h... yes
checking for ANSI ioctl definitions... yes
checking for strerror... yes
checking for strlcpy... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking for library containing putmsg... none required
checking for ether_hostton... yes
checking whether ether_hostton is declared... no
checking netinet/ether.h usability... yes
checking netinet/ether.h presence... yes
checking for netinet/ether.h... yes
checking whether ether_hostton is declared... yes
checking if --disable-protochain option is specified... enabled
checking packet capture type... linux
checking for getifaddrs... yes
checking ifaddrs.h usability... yes
checking ifaddrs.h presence... yes
checking for ifaddrs.h... yes
checking if --enable-ipv6 option is specified... no
checking whether to build optimizer debugging code... no
checking whether to build parser debugging code... no
checking Linux kernel version... 3
checking if if_packet.h has tpacket_stats defined... yes
checking whether we have /proc/net/dev... yes
checking whether we have DAG API headers... no (/usr/local/include)
checking for ranlib... ranlib
checking if sockaddr struct has sa_len member... no
checking if sockaddr_storage struct exists... yes
checking if dl_hp_ppa_info_t struct has dl_module_id_1 member... no
checking if unaligned accesses fail... no
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h

Configuration complete: 
         Compiling for: linux-gnu (x86_64)
   Installing as group: root
    Man pages owned by: man
       Installing into: /usr/local
        Setuid capable: yes
         Zaurus extras: no
      Terminal Control: ncurses
      Curses interface: yes
      Panels interface: yes
 Linux Netlink capture: no
       Linux wireless : no
 Linux wireless v.22+ : no
          pcap capture: yes
           pcap source: libpcap-0.9.1-kis
        WSP100 capture: no
          Viha capture: no
      Radiotap headers: no
 Using local dump code: yes
Using ethereal wiretap: no
   Imagemagick support: no
         Expat Library: no
           GMP Library: no
       PThread Support: yes
      libz compression: no
*** WARNING ***
Linux Wireless Extentions were not found.  This means that they are not
turned on in your kernel or that your kernel source include paths on your
distribution are broken (namely, that linux/wireless.h didn't exist or
was unuseable).  Without wireless extentions, most of the commonly used
packet sources (such as Cisco, Orinoco, Madwifi, Prism54, and others)
WILL NOT BE BUILT.
*** WARNING ***

Configuration complete.  Run 'make dep' to generate dependencies
and 'make' followed by 'make install' to compile and install.

gunners@AFC:~/Downloads/kismet-2005-06-R1$ make dep
Makefile:371: .depend: No such file or directory
Generating dependencies... 
make[1]: Entering directory `/home/gunners/Downloads/kismet-2005-06-R1'
make[2]: Entering directory `/home/gunners/Downloads/kismet-2005-06-R1'
make[2]: `.depend' is up to date.
make[2]: Leaving directory `/home/gunners/Downloads/kismet-2005-06-R1'
make[1]: Leaving directory `/home/gunners/Downloads/kismet-2005-06-R1'



gunners@AFC:~/Downloads/kismet-2005-06-R1$ make
g++ -Ilibpcap-0.9.1-kis -O2 -Wall -DVERSION_MAJOR=\"2005\" -DVERSION_MINOR=\"06\" -DVERSION_TINY=\"R1\" -DTIMESTAMP=\"`cat TIMESTAMP`\" -g -O2 -g -O2 -c util.cc -o util.o 
In file included from util.cc:21:0:
util.h:68:2: warning: &#8216;typedef&#8217; was ignored in this declaration [enabled by default]
util.cc: In function &#8216;int Hex2UChar(unsigned char*, unsigned char*)&#8217;:
util.cc:116:57: error: &#8216;memset&#8217; was not declared in this scope
util.cc: In function &#8216;int RunSysCmd(char*)&#8217;:
util.cc:251:19: warning: ignoring return value of &#8216;int system(const char*)&#8217;, declared with attribute warn_unused_result [-Wunused-result]
make: *** [util.o] Error 1

```


Thank you for taking the time to read through this, and any help would be greatly appreciated as im not sure where the issue is lying.

Thanks again :)

---

### Post by chili555 on 2012-01-25
A kismet server on a WRT54 is pretty sophisticated stuff for a person who says 'im a noob with linux and still trying to learn my ways.' The best way to learn your ways is to churn through this and learn it with a minimum of help. How much could you learn if someone just gave you the answer (assuming I had one!) 

I suggest you go back to the first place you got a warning; here:> onfigure: WARNING: *** Missing Linux netlink headers. wlanng_legacy source will not be built. ***Now check in Synaptic Package Manager. Usually in 'configure' files, headers files really means -dev files. On my system, when I search for netlink, I see I have several packages installed that reference netlink, libnl3 for only one example. I do NOT have libnl3[COLOR="Red"]-dev[/COLOR] installed. I'd suggest you install it and a few other likely looking netlink -dev packages. Now run 'configure' again. Did you get rid of that warning? Great!

Now here's the next warning:> configure: WARNING: *** Missing Linux Wireless kernel extentions. The majority of packet sources on Linux require this support and will not work without it. Make sure your kernel header packages are installed. If all else fails, try the --with-linuxheaders directive. ***I'd install linux-headers-generic and run 'configure' again. Did you get rid of that warning? Great!

Keep going using Synaptic and a bit of detective work and get rid of all the other warnings and errors in 'configure.' *NOW* run 'make' and see if you don't have a more harmonious result.

---

### Post by rmortim on 2012-01-25
Thanks chilli555, Ill give that a go and see what i get.

Well i know a fair bit about networking and setting up routers and still busy learning everyday as im still a student.but mostly it has always been windows based. So im new to the whole linux. the previous errors I recieved i managed to find how to resolve on google. but unfortunately couldnt find much to this, I do appreciate your suggestions and have actually learnt some new things from your reply in regards to headers mean -dev files.

Thanks again. ill reply my results

---

### Post by chili555 on 2012-01-25
I'll be ready to help. Good luck!

---

### Post by rmortim on 2012-01-25
Hi Chili555

Through synaptics i installed libnl3-dev but still got the same errors.

To install the libnl2-dev or libnl-dev packages it removes the other packages, but even with trying that i still get the same errors, 

I looked at linux headers under synaptics but not sure if any of those would need to be installed.

I can see a few threads with the same issue, but none resolved or have any replys.

Thanks again

---

### Post by rmortim on 2012-01-25
I came across this thread where someone had the same errors, 

[http://forums.freebsd.org/showthread.php?t=2217](http://forums.freebsd.org/showthread.php?t=2217)

But doesnt say exactly how he fixed it, Execpt that it was the bsd radiotap setting? He was using freebsd but would something like that help?

But cant seem to find anything on how to get that setting working?

---

### Post by chili555 on 2012-01-25
> Through synaptics i installed libnl3-dev but still got the same errors.Did you look at other netlink packages and, of course the -dev packages? For instance, I might look at libnfnetlink0 and others. Depending on your kernel version, I believe libnl3 and libnl3-dev are most appropriate. I'd revert to those and remove 2.

Is there a README that discusses prerequisites? I know, I know, we usually don't care about no steenking README, but sometimes it helps.> I looked at linux headers under synaptics but not sure if any of those would need to be installed.Well, I am; linux-headers-generic will figure out what you need and not only install it but keep it updated.

Please install libnl3, libnl3-dev and linux-headers-generic and show me the 'configure' after that.

Out of curiousity, why did you select the 2005 version of kismet and not the 2008 version in Synaptic. You may be right, I just don't understand.

---

### Post by rmortim on 2012-01-25
I have all 3 of those installed.
Well i have kernal 3.0.0.12 on this machine and see that linux-headers-3.0.0.12-genirc is installed.

There is still a linus-generic-headers and when i install that it upgrades it to version 3.0.0.15 but also gives the same results when i configure.

The reason i chose these versions is because im running DD-wrt and found the how to instructions using those old kismet files, as those releases had a Kismet-Drone release for the wrt54gl. so i thought it would be easier to get those same version files as the drone for the server than the new version to connect to the drone.

Also i cant find a kismet_drone file in the newer versions

I can try install the new version on kismet but the config file is slightly diffrent, I have read the readme file, but it doesnt say anything about the errors im getting, 

thanks again

---

### Post by chili555 on 2012-01-25
> I have read the readme file, but it doesnt say anything about the errors im getting, Can you please post it here as an attachment using the paperclip tool at the top of the reply box? Can you give me a link to the file you downloaded?

---

### Post by rmortim on 2012-01-25
Here is the links for the kismet drone and server
Drone:
[http://www.kismetwireless.net/code/kismet-2005-06-R1a-wrt54.tar.gz](http://www.kismetwireless.net/code/kismet-2005-06-R1a-wrt54.tar.gz)
Server:
[http://www.kismetwireless.net/code/kismet-2005-06-R1.tar.gz](http://www.kismetwireless.net/code/kismet-2005-06-R1.tar.gz)

You can see all there versions and downloads at
[http://www.kismetwireless.net/code/](http://www.kismetwireless.net/code/)

There is a readme file in the downloads but can also be viewed at
[http://www.kismetwireless.net/documentation.shtml](http://www.kismetwireless.net/documentation.shtml)

Other pages that i have been using as a reference 
[http://www.dd-wrt.com/wiki/index.php/Wrt54g_kismet_with_linux_server](http://www.dd-wrt.com/wiki/index.php/Wrt54g_kismet_with_linux_server)

the problem with using the newcore(the newer versions) is that it uses different protocol or something, when editing the kismet.conf the source is alot different,

Thanks, Ive got 2 of the wrt54gl's so i thought of maybe trying with openwrt on the other one but then again the problem is with server and not the drone.

---

### Post by chili555 on 2012-01-26
I never like to say 'I don't know' but I am getting close. I am just not sure if it's possible to install a 2005 version of Kismet on a 3.0xx kernel. I've tried a lot of things but had no better success than you. The only thing I can suggest is maybe trying again with an older Ububtu version: 10.04LTS uses 2.6.32, if I remember correctly.

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

I wish I could be of more assistance.

---

### Post by rmortim on 2012-01-26
Haha, Well thank for trying anyway, i think ill just try openwrt with aircrack-ng first...
If thats not to my liking i can always try install the server and drone on the wrt54gl and do a SD card mod.

Otherwise an older version of ubuntu would be the way to go. 
Thanks again

---

