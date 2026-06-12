---
title: "DLink DWA-125 on Natty"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by veryaner on 2011-09-12
Hi everybody, first of all, thanks for any help.

I bought the wireless DWA-125 adapter, in the beginning it was working fine, suddenly, I cannot say after what event, it started to work very slowly, the connection really slowed down. 
I searched on the internet and in the forum and I tried almost all the suggestions, but I cannot get it to work again. 

Any help is appreciated.

I'm running on 11.04 version.

---

### Post by lkjoel on 2011-09-12
Could you run the Network Info script (in my signature), and attach the generated file?

---

### Post by veryaner on 2011-09-14
Sorry for the delay I had too much work.

The file is attached.

Thanks for the help.

---

### Post by lkjoel on 2011-09-17
It looks like as if you don't have any internet on your DWA-125

---

### Post by lkjoel on 2011-09-17
Try following this guide: [http://lkubuntu.wordpress.com/2011/09/09/how-to-compile-rt2870sta-successfully/](http://lkubuntu.wordpress.com/2011/09/09/how-to-compile-rt2870sta-successfully/)

---

### Post by mym2f on 2011-09-18
Hi there .......
I am a new user of Ubuntu (64-bit) system

I can see that you have links to some amazing guides .... ^_^

Please help me to get my DWA-126 usb adapter working so that I can crack some WPAs !!

 My Ubuntu is installed through VMware player and its kernel version is
 2.6.38-11-generic.

 The problem is that the interface is not detected (when using iwconfig).
 But it seems that the device itself is detected bcuz when using lsusb
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 002: ID 071d:3a10 D-Link System
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

uname -a
 Linux ubuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

 modinfo ar9170 | grep 3A10
 ERROR: modinfo: could not find module ar9170

 modinfo car9710 | grep 3a10
 ERROR: modinfo: could not find module car9710

 modinfo ath9k_htc | grep 3A10
 alias: usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*

Thank you

---

### Post by lkjoel on 2011-09-19
> **mym2f said:**
> Hi there .......
I am a new user of Ubuntu (64-bit) system

I can see that you have links to some amazing guides .... ^_^

Please help me to get my DWA-126 usb adapter working so that I can crack some WPAs !!

 My Ubuntu is installed through VMware player and its kernel version is
 2.6.38-11-generic.

 The problem is that the interface is not detected (when using iwconfig).
 But it seems that the device itself is detected bcuz when using lsusb
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 002: ID 071d:3a10 D-Link System
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

uname -a
 Linux ubuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

 modinfo ar9170 | grep 3A10
 ERROR: modinfo: could not find module ar9170

 modinfo car9710 | grep 3a10
 ERROR: modinfo: could not find module car9710

 modinfo ath9k_htc | grep 3A10
 alias: usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*

Thank you
FYI, Cracking secured networks are illegal in some countries.
If you still want to get your wireless stick working, could you give me the output of this command?
```
lsusb -vs  071d:3a10

```

---

### Post by mym2f on 2011-09-19
Hi again ....

Nothing appears when writing that code ....

---

### Post by lkjoel on 2011-09-20
Once the device is plugged in, give me the output of:
```
lsusb -vs 071d:3a10

```

---

