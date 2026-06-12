---
title: "Unable to connect to WiFi after update to 13.04."
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by Archit88 on 2013-05-06
Hello all,
i recently updated my Ubuntu from 12.10 to 13.04, The problem is when ever i restart my laptop i am unable to connect to internet. So what i do is i install "bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64" from installation cd,  every time i reboot.
is there is possible permanent solution for this?

*WiFi Signal strength is strong all the times.


Network details

```
 sudo lshw -C network


 *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: c0:18:85:58:5d:f1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 ip=192.168.6.246 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:c2500000-c2503fff



```

thanks :D

---

### Post by varunendra on 2013-05-06
Hi Archit!

Please post output of :
```
lspci -nn | grep 0280
```
If it is "..... BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] ...", then try this post : [http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619)

**PS:**
By the way, which installation cd do you install those packages from? Because they are not on my 13.04 DVD, instead a newer version.

---

### Post by Archit88 on 2013-05-06
```
 lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

I am using that package from Ubuntu 12.10 ,can found it under ```
pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb 
```

---

### Post by varunendra on 2013-05-06
> **Archit88 said:**
> I am using that package from Ubuntu 12.10 ,can found it under ```
pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb 
```

Hmm.. suspected that. Please try the post I linked to, post back the result or errors if there are any. Thanks!

---

### Post by Archit88 on 2013-05-06
Until driver compilation every thing was alright

```
[COLOR=#000000][FONT=Ubuntu Mono]cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless[/FONT][/COLOR]
```

my modules folder showing me this 
```
3.5.0-17-generic  3.5.0-27-generic  3.8.0-19-generic
```
where to copy?

---

### Post by Hadaka on 2013-05-06
Hi, it should copy by it's self with the command


[COLOR=#000000][FONT=Ubuntu Mono]cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless[/FONT][/COLOR]

leave `uname-r` just the way it is, no need to fill in any data.

post back if you have any more errors.

thanks.

---

### Post by Archit88 on 2013-05-08
[SOLVED]

Thank you @varunendra , @Hadaka

---

