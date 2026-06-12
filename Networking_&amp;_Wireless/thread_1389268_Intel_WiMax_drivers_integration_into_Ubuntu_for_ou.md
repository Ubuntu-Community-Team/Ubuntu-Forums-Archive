---
title: "Intel WiMax drivers integration into Ubuntu for out-of-the-box support"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by Atakua on 2010-01-24
Recently I have obtained a netbook with Intel WiMax wireless card. Now this PC has a fresh installation of Karmic. After some searching through the net I found that enabling WiMaX requires some additional steps involving compilation of drivers/userland programs taken from official Intel site [http://linuxwimax.org](http://linuxwimax.org) .

I checked the installation and found that while kernel components are already here(e.g. kernel modules /[FONT="Courier New"]lib/modules/2.6.31-17-generic/kernel/drivers/net/wimax/i2400m/i2400m-usb.ko[/FONT] and firmware [FONT="Courier New"]/lib/firmware/i2400m-fw-usb-1.4.sbcf[/FONT]) userland utilities are not. The required programs include [FONT="Courier New"]wimaxd[/FONT], the daemon, and [FONT="Courier New"]wimaxcu[/FONT] supplicant. 

Though it is not a big problem for me to perform all the biulding process myself, I think certain novice users will be too confused with this and unable to bring Wimax interface up.
I think that it would be nice if some package for these tools existed in some (un)official repository.

The best thing is to integrate this functionality (starting daemons, supplicants, configuring interfaces through GUI) in network interface framework.

Here are links to some external sites describing the process:

[LIST]
[http://linuxwimax.org]("http://linuxwimax.org") - an official site with sources/firmware.
[/LIST]
[LIST]
[http://habrahabr.ru/blogs/linux/77385/]("http://habrahabr.ru/blogs/linux/77385/") - HOWTO for Russian "Yota" Wimax operator (in Russian).
[/LIST]
[LIST][http://lists.linuxwimax.org/pipermail/wimax/2009-February/000469.html]("http://lists.linuxwimax.org/pipermail/wimax/2009-February/000469.html") - mailing list post with description of setup on x86_64 machine.
[/LIST]

---

### Post by ericwwheeler on 2011-02-02
Could you post a quick howto via command line to install wimax-tools, etc?

---

### Post by Atakua on 2011-02-03
> **ericwwheeler said:**
> Could you post a quick howto via command line to install wimax-tools, etc?

Well, it seems that Intel has refreshed the Wimax drivers since I set them up at my netbook. As far as I can see at [http://linuxwimax.org](http://linuxwimax.org)  in version 1.5 they switched from a separate binary supplicant to common WPA supplicant + patch .

At [http://linuxwimax.org/Download](http://linuxwimax.org/Download) they have a bunch of well written README's describing how to set the things up.

I only usded version 1.4, so my experience is not of much value anymore I am afraid. 

The only thing that might be omitted at that site is that one will commonly need a special ISP configs to connect to a particular network. In my case they were called NDnSAgentDefaultConfig.xml and NDnSAgentConfig_forDriver.xml and one could find them at the install CD or on the Net. 

That's all what I can say to help you at the moment, sorry.

---

### Post by ericwwheeler on 2011-07-11
Hey Atakua, were you successful getting the wimax to work? It appears that linuxwimax.org is down. Any help would be appreciated

---

### Post by Atakua on 2011-07-12
> **ericwwheeler said:**
> Hey Atakua, were you successful getting the wimax to work? It appears that linuxwimax.org is down. Any help would be appreciated
Yes. I actually updated my system to 10.10 and had to reinstall Wimax drivers. So I used a new 1.5.x branch. After installation I even noticed that the "user experience" of using them has improved - I no longer need special manipulations in order to obtain IP for wmx0 - just `sudo wimaxcu ron` does the whole thing.

The compilation is quite a trick though - you need to know how to use `make` and `patch` tools and install stuff from source code. An no support from Network Manager so far - everything is done from command line in my case.

[http://linuxwimax.org](http://linuxwimax.org) is down for me as well at the moment. It worked a monthe ago though. So you can try an Internet Wayback Machine or Google cached pages to grab a snapshot of it.

---

### Post by phi1ip on 2011-10-06
I wonder if Ubuntu is working out of the box in Moscow yet for Yota, on such a netbook as lenovo 10 S2?

or generally is Yota (WiMax) working out of the box?

in 11.04 or will it be in 11.10?

---

### Post by Atakua on 2011-10-06
> **phi1ip said:**
> I wonder if Ubuntu is working out of the box in Moscow yet for Yota, on such a netbook as lenovo 10 S2?

or generally is Yota (WiMax) working out of the box?

in 11.04 or will it be in 11.10?

Just as I said before - no, it won't work out of the box. While 11.04's kernel supports Intel Wifi/Wimax hardware out of the box I had to compile/install userland utilities myself. No GUI support too.

I haven't tried Samsung Wimax dongles so far but I am pretty sure the same thing holds for them too, except that drivers/utilities have to be installed from a different source.

---

### Post by Atakua on 2011-10-06
Oh, and for the record - at the moment I no longer own any Wimax devices so I cannot check if stuff still works with new versions of Ubuntu and/or Intel Wimax drivers.

---

### Post by smrahmani on 2011-11-22
If the problem solved, please tell me too :).

---

### Post by Oleksa Stasevych on 2012-04-05
In order my wimax Inter 6250 Centrino can be managed I need to re-compile Network Manager. It was quite easy before I upgraded to the last Ubuntu 12.04 Beta2. The version of network-manager in 0.9.4.0

While compiling it I faced with the error during compilation with **libdns-manager**:

> $ make check
Making check in dns-manager make[3]: &#1042;&#1093;&#1086;&#1078;&#1091; &#1091; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075; "/home/stasevych/install/network-manager/nm0.9.4.0/network- manager-0.9.4.0/src/dns-manager" /bin/bash ../../libtool  --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../..   -I../../src/logging -I../../libnm-util -I../../libnm-util -I../../src -I../../include -I../../include -I/usr/include/libnl3   -I/usr/include/libnl3   -I/usr/include/libnl3   -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include   -DLOCALSTATEDIR=\"/var\"   -Wall -std=gnu89 -g -O2 -Wshadow -Wmissing-declarations -Wmissing-prototypes -Wdeclaration-after-statement -Wfloat-equal -Wno-unused-parameter -Wno-sign-compare -fno-strict-aliasing -Wno-unused-but-set-variable -Wundef -Werror -MT libdns_manager_la- 
nm-dns-dnsmasq.lo -MD -MP -MF .deps/libdns_manager_la-nm-dns-dnsmasq.Tpo -c -o libdns_manager_la-nm-dns-dnsmasq.lo `test -f 'nm-dns-dnsmasq.c' || echo './'`nm-dns-dnsmasq.c libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../.. -I../../src/logging -I../../libnm-util -I../../libnm-util -I../../src -I../../include -I../../include -I/usr/include/libnl3 -I/usr/include/libnl3 -I/usr/include/libnl3 -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -DLOCALSTATEDIR=\"/var\" -Wall -std=gnu89 -g -O2 -Wshadow -Wmissing-declarations -Wmissing-prototypes -Wdeclaration-after-statement -Wfloat-equal -Wno-unused-parameter -Wno-sign-compare -fno-strict-aliasing -Wno-unused-but-set-variable -Wundef -Werror -MT libdns_manager_la-nm-dns-dnsmasq.lo -MD -MP -MF .deps/libdns_manager_la-nm-dns-dnsmasq.Tpo -c nm-dns-dnsmasq.c  -fPIC -DPIC -o .libs/libdns_manager_la-nm-dns-dnsmasq.o 
nm-dns-dnsmasq.c: In function 'update': nm-dns-dnsmasq.c:274:2: error: passing argument 1 of 'g_slist_copy' discards 'const' qualifier from pointer target type [-Werror] /usr/include/glib-2.0/glib/gslist.h:82:10: note: expected 'struct GSList *' but argument is of type 'const struct GSList *'
cc1: all warnings being treated as errors
make[3]: *** [libdns_manager_la-nm-dns-dnsmasq.lo] &#1055;&#1086;&#1084;&#1080;&#1083;&#1082;&#1072; 1
Has anybody faced with similar error or know how to solve it? Many thanks in advance.

---

