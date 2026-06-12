---
title: "Setup Trendnet USB 2.0 wireless adapter on an AMD64 system ?"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by cemptor on 2006-02-15
Have been struggling to install a Trendnet TEW 424UB 802.11g USB 2.0 adapter on my Opteron 144 based desktop under Ubuntu Linux (Dapper Drake Flight4).  Can't find a native driver, so I tried ndiswrapper with a SiS 163u driver for AMD64, and it's not working. It can recognize the hardware, but am unable to load ndiswrapper.

Anything I can do, short of abandoning and buying another adapter?

I downloaded the ndiswrapper source (version 1.10), made a debian package, and installed it. Also tried it with the pre-installed ndiswrapper 1.8 that came with Drake flight 4

installed the sis163u.inf (downloaded from [www.sis.com/download](www.sis.com/download) ) driver for AMD64 using ndiswrapper, after editing the control files to replace i386 with amd64. The driver according to release notes supprts Windows XP_64 and vista.

ndiswrapper -l
sis163u driver installed, hardware present

depmod  -a
no errors

When I run modprobe ndiswrapper, It hangs, and 
dmesg gives me an error message that "loadndiswrapper could not be loaded."

Help!

---

### Post by cemptor on 2006-03-14
On a whim, I tried to install the 32 bit driver under a Dapper Drake i386 live CD, and it works with ndiswrapper.

I don't want to waste my new hardware and go to 32 bit, just for the sake of this cheap card. Any ideas?

If I were to buy a new wireless g adapter, which one should I pick that will work in a 64 bit environment? Preferably one with native Linux 64 bit driver.

Thanks

---

