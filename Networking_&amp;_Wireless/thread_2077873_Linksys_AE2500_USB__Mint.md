---
title: "Linksys AE2500 USB / Mint"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by kennjason on 2012-10-29
Hi, all.

I think (I hope!) I've scoured the internet and looked through every forum post I could find in regards to this, and I'm still completely stumped. 

I'm running Mint 13:

```
jason@boo ~ $ uname -a
Linux boo 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:32:50 UTC 2012 i686 i686 i386 GNU/Linux
jason@boo ~ $ 
``````
jason@boo ~ $ uname -m
i686
jason@boo ~ $ 

``````
jason@boo /etc $ cat /etc/issue
Linux Mint 13 Maya \n \l
jason@boo /etc $ 

```I have a Cisco AE2500 USB wireless stick that SEEMS like it's recognized by the system: 

```
jason@boo /etc $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 13b1:003a Linksys AE2500 802.11abgn Wireless Adapter [Broadcom BCM43236]
Bus 003 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 003 Device 004: ID 045e:0752 Microsoft Corp. 
jason@boo /etc $ 

``````
jason@boo /etc $ ndiswrapper -l
bcmwlhigh5 : driver installed
        device (13B1:003A) present
jason@boo /etc $ 

```Except that it doesn't work. Troubleshooting & forum browsing has led me to believe that perhaps I'm running the wrong version of ndiswrapper, as I get this: 

```
jason@boo /etc $ ndiswrapper -v
ERROR: modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
ERROR: modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net

```The problem is, I went to Sourceforge and picked up the 1.58 version and followed instructions and I get this far: 

```
jason@boo /usr/src/ndiswrapper-1.58rc1 $ sudo make
make -C utils
make[1]: Entering directory `/usr/src/ndiswrapper-1.58rc1/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/usr/src/ndiswrapper-1.58rc1/utils'
make -C driver
make[1]: Entering directory `/usr/src/ndiswrapper-1.58rc1/driver'
Makefile:36: *** Cannot find kernel version in /lib/modules/3.2.0-32-generic/build, is it configured?.  Stop.
make[1]: Leaving directory `/usr/src/ndiswrapper-1.58rc1/driver'
make: *** [driver] Error 2
jason@boo /usr/src/ndiswrapper-1.58rc1 $ 

```Any ideas? I've been using links from here, and from these sites as well: 

[http://www.grailbox.com/2012/05/installing-cisco-linksys-ae2500-wireless-adapter-in-linux/](http://www.grailbox.com/2012/05/installing-cisco-linksys-ae2500-wireless-adapter-in-linux/)

[http://tinymelinux.com/forum/thread-865-post-3760.html#pid3760](http://tinymelinux.com/forum/thread-865-post-3760.html#pid3760)

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

My thanks in advance!

-Jason

---

### Post by kennjason on 2012-11-02
I managed to fix it, you can close this thread. 

Solution: I installed Ubuntu 12.10 instead of Mint. Works fine now.

---

