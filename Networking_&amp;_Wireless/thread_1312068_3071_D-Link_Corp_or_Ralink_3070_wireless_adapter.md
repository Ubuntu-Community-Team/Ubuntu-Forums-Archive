---
title: "3071 D-Link Corp or Ralink 3070 wireless adapter"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by _mikec_ on 2009-11-02
i am using ubuntu desktop v8.04, trying to install a wireless usb adapter with chipset ralink 3070.  I have some of the things previous users tried to make the adapter work but no success. here's what i tried so far.

downloaded: 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2
tar xvfj 2009_0525_RT3070_Linux_STA_v2.1.1.0.bz2

sudo nano os/linux/config.mk
"change"
> HAS_WPA_SUPPLICANT=n
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=nto 

> HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=ysudo nano /etc/modules
added: Alias ra0 rt3070sta

save & closed
sudo make && sudo make install

i get this error:
> mk: 68: CROSS_COMPILE: not found os/linux/config.
mk: 68: CC: not found os/linux/config.
mk: 69: CROSS_COMPILE: not found os/linux/config.
mk: 69: LD: not found os/linux/config.
mk: 74: WFLAGS: not found os/linux/config.
mk: 76: Syntax error: word unexpected (expecting ")")lsusb shows:
**Bus 002 Device 004: ID 07b8:3071 D-Link Corp. **
why does it say D-Link Corp with model 3071 anyways ?

Can somebody help me figure this thing out please, i do not know what to do next..

---

### Post by _mikec_ on 2009-11-04
bump

---

### Post by _mikec_ on 2009-11-26
solution: 
sudo nano /etc/modprobe.d/blacklist.conf

add:
blacklist rt2800usb

save/exit/reboot
ubuntu 9.10

---

### Post by fvpetrov on 2009-11-30
woks also with my no-name wireless adapter ralink 3071
(lsusb: Bus 001 Device 002: ID 148f:3071 Ralink Technology, Corp.)

ubuntu 9.10

---

### Post by lonniehenry on 2010-03-09
_mikec_ Thanks for the info about the blacklist driver info. I got a mvix nubbin.  I just used it and it work beautifully on Lucid.

---

### Post by jasonwert on 2010-07-06
> **lonniehenry said:**
> _mikec_ Thanks for the info about the blacklist driver info. I got a mvix nubbin.  I just used it and it work beautifully on Lucid.


Are you getting N type speeds with the MVIX Nubbin? I've never been able to get anything beyond 56Mbps

-jason

---

### Post by lonniehenry on 2010-07-16
I have only been able to connect at 56 altho it says it will connect at 150 max. It connects at 78 on a win7 machine.  I have tried to figure out how to make it connect faster but haven't had much luck.

---

