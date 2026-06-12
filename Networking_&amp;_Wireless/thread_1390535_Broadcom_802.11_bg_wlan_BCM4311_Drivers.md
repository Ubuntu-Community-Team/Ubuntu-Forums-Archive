---
title: "Broadcom 802.11 b/g wlan BCM4311 Drivers"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by Dante1217 on 2010-01-25
I know this has been posted before.. but every topic i looked at gave me no help


lspci output:

```
02:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
    Subsystem: Hewlett-Packard Company Device 1374
    Flags: fast devsel, IRQ 16
    Memory at f4000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: ssb

```

i was having issues with the STA drivers located here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)


the issue was, on this line:
```
sudo insmod wl.ko
```

it returned:

```
insmod: error inserting 'wl.ko': -1 File exists
```

Any help is greatly appriciated.

](*,)

---

### Post by bkratz on 2010-01-25
Maybe there is something here

[http://ubuntuforums.org/showthread.php?t=896713&highlight=sudo+insmod+wl.ko](http://ubuntuforums.org/showthread.php?t=896713&highlight=sudo+insmod+wl.ko)

---

### Post by JBAlaska on 2010-01-25
Are you using Karmic? There is STA driver support built in. Some people have trouble getting the STA driver to "Show up" in hardware drivers. 

If this the case for you, type the following in a terminal:
```
sudo apt-get install bcmwl-kernel-source
```

Now reboot, and go to System, Administration, Hardware Drivers.

And you should be able to select the STA driver.

[COLOR="Red"]Edit: you either have to have a wired connection for the above to work, or you can put the LiveCD in your drive and go to: System, Administration, Software sources and check the box below "Installable from CDROM". Then open a term and do:[/COLOR]
```
sudo apt-get update
```
[COLOR="Red"]Then:[/COLOR]
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by Dante1217 on 2010-01-25
Thank you JB, worked like a charm.:D

---

