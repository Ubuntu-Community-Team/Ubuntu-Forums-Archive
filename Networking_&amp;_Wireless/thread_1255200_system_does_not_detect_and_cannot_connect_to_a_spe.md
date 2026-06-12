---
title: "system does not detect and cannot connect to a specific network"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by redsun82 on 2009-09-01
Hi.

Network manager was working just fine on my Lenovo X300, connecting to my airport express WPA2 network. Then since some days out of the blue it does not detect the network at all: it lists a lot of other networks (included some WPA protected ones), can connect to the unprotected ones I tested, but nothing for mine. It is neither visible nor manually connectable.

The network is not hidden, and both another windows machine and my android device connect just fine. I tried fiddling with the airport express base (resetting, turning off protection, downgrading and upgrading again the firmware), and also switched momentarily to wicd to find the same problem. 

Just once and with no apparent reason the network was visible, but I could not connect to it as it was detected by NM as WEP, but even setting WPA protection manually it failed. Then again with no apparent reason it disappeared again.

I'm really baffled. I did quite a big update the 28th that might have broken something, but nothing apparently linked with network manager (though I don't know the packages enough, especially the lib ones).

lspci gives the following for my card
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```

I run Linux Mint, latest distribution. mintUpdate keeps a log of the updates, so here are my latest ones:
```
28 ago 2009 15:34:01	pidgin	2	1:2.5.5-1ubuntu8.3	1:2.5.5-1ubuntu8.4
28 ago 2009 15:34:01	thunderbird	2	2.0.0.22+build1+nobinonly-0ubuntu0.9.04.1	2.0.0.23+build1+nobinonly-0ubuntu0.9.04.1
28 ago 2009 15:34:01	kdelibs5-data	3	4:4.2.2-0ubuntu5	4:4.2.2-0ubuntu5.1
28 ago 2009 15:34:01	libglu1-mesa	3	7.4-0ubuntu3.1	7.4-0ubuntu3.2
28 ago 2009 15:34:01	libmono-system-web2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libmono-system2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	apache2-utils	3	2.2.11-2ubuntu2.2	2.2.11-2ubuntu2.3
28 ago 2009 15:34:01	libmono-posix2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libprotobuf3	3	2.0.3-0ubuntu2	2.0.3-2.2ubuntu1~jaunty1
28 ago 2009 15:34:01	mono-2.0-gac	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	mozilla-thunderbird	3	2.0.0.22+build1+nobinonly-0ubuntu0.9.04.1	2.0.0.23+build1+nobinonly-0ubuntu0.9.04.1
28 ago 2009 15:34:01	tzdata	3	2009j-0ubuntu0.9.04	2009l-0ubuntu0.9.04
28 ago 2009 15:34:01	libmono-cairo2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	pidgin-data	3	1:2.5.5-1ubuntu8.3	1:2.5.5-1ubuntu8.4
28 ago 2009 15:34:01	libpurple0	3	1:2.5.5-1ubuntu8.3	1:2.5.5-1ubuntu8.4
28 ago 2009 15:34:01	apache2-mpm-prefork	3	2.2.11-2ubuntu2.2	2.2.11-2ubuntu2.3
28 ago 2009 15:34:01	libmono-getoptions2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libpurple-bin	3	1:2.5.5-1ubuntu8.3	1:2.5.5-1ubuntu8.4
28 ago 2009 15:34:01	mono-runtime	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libmono-system-data2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	mono-gac	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libgnutls26	3	2.4.2-6	2.4.2-6ubuntu0.1
28 ago 2009 15:34:01	libmono-sharpzip2.84-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libplasma3	3	4:4.2.2-0ubuntu5	4:4.2.2-0ubuntu5.1
28 ago 2009 15:34:01	kdelibs5	3	4:4.2.2-0ubuntu5	4:4.2.2-0ubuntu5.1
28 ago 2009 15:34:01	php5	3	5.2.6.dfsg.1-3ubuntu4.1	5.2.6.dfsg.1-3ubuntu4.2
28 ago 2009 15:34:01	libmono-data2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	mesa-utils	3	7.4-0ubuntu3.1	7.4-0ubuntu3.2
28 ago 2009 15:34:01	libcurl3-gnutls	3	7.18.2-8ubuntu4	7.18.2-8ubuntu4.1
28 ago 2009 15:34:01	apache2.2-common	3	2.2.11-2ubuntu2.2	2.2.11-2ubuntu2.3
28 ago 2009 15:34:01	mono-jit	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libvorbis0a	3	1.2.0.dfsg-3.1	1.2.0.dfsg-3.1ubuntu0.9.04.1
28 ago 2009 15:34:01	apache2	3	2.2.11-2ubuntu2.2	2.2.11-2ubuntu2.3
28 ago 2009 15:34:01	libmono-data-tds2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libmjpegtools-1.9	3	1:1.9.0-0.0	1:1.9.0-0.0ubuntu3
28 ago 2009 15:34:01	libvorbisenc2	3	1.2.0.dfsg-3.1	1.2.0.dfsg-3.1ubuntu0.9.04.1
28 ago 2009 15:34:01	php5-common	3	5.2.6.dfsg.1-3ubuntu4.1	5.2.6.dfsg.1-3ubuntu4.2
28 ago 2009 15:34:01	kdelibs-bin	3	4:4.2.2-0ubuntu5	4:4.2.2-0ubuntu5.1
28 ago 2009 15:34:01	libvorbisfile3	3	1.2.0.dfsg-3.1	1.2.0.dfsg-3.1ubuntu0.9.04.1
28 ago 2009 15:34:01	kdelibs4c2a	3	4:3.5.10.dfsg.1-1ubuntu8	4:3.5.10.dfsg.1-1ubuntu8.1
28 ago 2009 15:34:01	kdelibs-data	3	4:3.5.10.dfsg.1-1ubuntu8	4:3.5.10.dfsg.1-1ubuntu8.1
28 ago 2009 15:34:01	libmono-i18n2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libmono-sqlite2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	app-install-data-partner	3	11.9.04.2	11.9.04.4
28 ago 2009 15:34:01	libmono2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libmono-corlib2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libapache2-mod-php5	3	5.2.6.dfsg.1-3ubuntu4.1	5.2.6.dfsg.1-3ubuntu4.2
28 ago 2009 15:34:01	mono-2.0-runtime	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libgl1-mesa-glx	3	7.4-0ubuntu3.1	7.4-0ubuntu3.2
28 ago 2009 15:34:01	libmono0	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	mono-common	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libmono-security2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:34:01	libgl1-mesa-dri	3	7.4-0ubuntu3.1	7.4-0ubuntu3.2
28 ago 2009 15:35:07	pidgin	2	1:2.5.5-1ubuntu8.3	1:2.5.5-1ubuntu8.4
28 ago 2009 15:35:07	thunderbird	2	2.0.0.22+build1+nobinonly-0ubuntu0.9.04.1	2.0.0.23+build1+nobinonly-0ubuntu0.9.04.1
28 ago 2009 15:35:07	kdelibs5-data	3	4:4.2.2-0ubuntu5	4:4.2.2-0ubuntu5.1
28 ago 2009 15:35:07	libglu1-mesa	3	7.4-0ubuntu3.1	7.4-0ubuntu3.2
28 ago 2009 15:35:07	libmono-system-web2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	libmono-system2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	apache2-utils	3	2.2.11-2ubuntu2.2	2.2.11-2ubuntu2.3
28 ago 2009 15:35:07	libmono-posix2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	libprotobuf3	3	2.0.3-0ubuntu2	2.0.3-2.2ubuntu1~jaunty1
28 ago 2009 15:35:07	mono-2.0-gac	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	mozilla-thunderbird	3	2.0.0.22+build1+nobinonly-0ubuntu0.9.04.1	2.0.0.23+build1+nobinonly-0ubuntu0.9.04.1
28 ago 2009 15:35:07	tzdata	3	2009j-0ubuntu0.9.04	2009l-0ubuntu0.9.04
28 ago 2009 15:35:07	libmono-cairo2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	pidgin-data	3	1:2.5.5-1ubuntu8.3	1:2.5.5-1ubuntu8.4
28 ago 2009 15:35:07	libpurple0	3	1:2.5.5-1ubuntu8.3	1:2.5.5-1ubuntu8.4
28 ago 2009 15:35:07	apache2-mpm-prefork	3	2.2.11-2ubuntu2.2	2.2.11-2ubuntu2.3
28 ago 2009 15:35:07	libmono-getoptions2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	libpurple-bin	3	1:2.5.5-1ubuntu8.3	1:2.5.5-1ubuntu8.4
28 ago 2009 15:35:07	mono-runtime	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	libmono-system-data2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	mono-gac	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	libgnutls26	3	2.4.2-6	2.4.2-6ubuntu0.1
28 ago 2009 15:35:07	libmono-sharpzip2.84-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	libplasma3	3	4:4.2.2-0ubuntu5	4:4.2.2-0ubuntu5.1
28 ago 2009 15:35:07	kdelibs5	3	4:4.2.2-0ubuntu5	4:4.2.2-0ubuntu5.1
28 ago 2009 15:35:07	php5	3	5.2.6.dfsg.1-3ubuntu4.1	5.2.6.dfsg.1-3ubuntu4.2
28 ago 2009 15:35:07	libmono-data2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	mesa-utils	3	7.4-0ubuntu3.1	7.4-0ubuntu3.2
28 ago 2009 15:35:07	libcurl3-gnutls	3	7.18.2-8ubuntu4	7.18.2-8ubuntu4.1
28 ago 2009 15:35:07	apache2.2-common	3	2.2.11-2ubuntu2.2	2.2.11-2ubuntu2.3
28 ago 2009 15:35:07	mono-jit	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	libvorbis0a	3	1.2.0.dfsg-3.1	1.2.0.dfsg-3.1ubuntu0.9.04.1
28 ago 2009 15:35:07	apache2	3	2.2.11-2ubuntu2.2	2.2.11-2ubuntu2.3
28 ago 2009 15:35:07	libmono-data-tds2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:07	libmjpegtools-1.9	3	1:1.9.0-0.0	1:1.9.0-0.0ubuntu3
28 ago 2009 15:35:07	libvorbisenc2	3	1.2.0.dfsg-3.1	1.2.0.dfsg-3.1ubuntu0.9.04.1
28 ago 2009 15:35:07	php5-common	3	5.2.6.dfsg.1-3ubuntu4.1	5.2.6.dfsg.1-3ubuntu4.2
28 ago 2009 15:35:07	kdelibs-bin	3	4:4.2.2-0ubuntu5	4:4.2.2-0ubuntu5.1
28 ago 2009 15:35:07	libvorbisfile3	3	1.2.0.dfsg-3.1	1.2.0.dfsg-3.1ubuntu0.9.04.1
28 ago 2009 15:35:07	kdelibs4c2a	3	4:3.5.10.dfsg.1-1ubuntu8	4:3.5.10.dfsg.1-1ubuntu8.1
28 ago 2009 15:35:07	kdelibs-data	3	4:3.5.10.dfsg.1-1ubuntu8	4:3.5.10.dfsg.1-1ubuntu8.1
28 ago 2009 15:35:08	libmono-i18n2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:08	libmono-sqlite2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:08	app-install-data-partner	3	11.9.04.2	11.9.04.4
28 ago 2009 15:35:08	libmono2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:08	libmono-corlib2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:08	libapache2-mod-php5	3	5.2.6.dfsg.1-3ubuntu4.1	5.2.6.dfsg.1-3ubuntu4.2
28 ago 2009 15:35:08	mono-2.0-runtime	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:08	libgl1-mesa-glx	3	7.4-0ubuntu3.1	7.4-0ubuntu3.2
28 ago 2009 15:35:08	libmono0	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:08	mono-common	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:08	libmono-security2.0-cil	3	2.0.1-4	2.0.1-4ubuntu0.1
28 ago 2009 15:35:08	libgl1-mesa-dri	3	7.4-0ubuntu3.1	7.4-0ubuntu3.2
31 ago 2009 14:17:07	python-gobject	3	2.16.1-1ubuntu2	2.16.1-1ubuntu3
```
It also purposedly leaves out some upgrades following the "don't fix it if it ain't broken" philosophy. Namely on my machine the following upgrades are not installed, maybe this can have somehing to do with the problem?
```
linux-headers-generic
linux-headers-2.6.28-15
libdbus-1-3
linux-libc-dev
dbus
libhal1
hal
linux-restricted-modules-common
libhal-storage1
grub-gfxboot
dbus-x11
linux-headers-2.6.28-15-generic
```

Hope someone can help me.

---

