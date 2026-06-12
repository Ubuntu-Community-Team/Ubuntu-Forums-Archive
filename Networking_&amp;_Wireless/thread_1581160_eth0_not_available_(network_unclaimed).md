---
title: "eth0 not available (network unclaimed)"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by bmwheaven on 2010-09-24
Hi,

I've been trying to get my realtek r8169 networkcard going, but haven't been successful yet. At first I saw the network card in the manager, but now it isn't visible anymore.
lshw gives this:

```
sudo lshw -class network
[sudo] password for ilir: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:09:02.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:f7fffc00-f7fffcff memory:f1000000-f101ffff(prefetchable)

```Can anyone help?
Thanks!

---

### Post by roccity1 on 2010-09-24
If you open a terminal and type lsmod does it show r8169 listed anyway? If not you can type sudo modprobe r8169 to load the driver.

---

### Post by bmwheaven on 2010-09-25
Nope, but it does show:
```
r8168                 109428  0
```That's because I tried this fix, but that didn't work:
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

---

### Post by bmwheaven on 2010-09-28
Anyone?

---

### Post by ngrieb on 2012-03-03
I get the same thing with a Gigabit 82578DC Ethernet controller. I have had to reboot my desktop every time I want to use the internet...for some reason a reboot makes the eth card be recognized. I have been searching everywhere trying to fix this annoying problem with no luck yet. I will keep searching though, because it is a large inconvenience.

---

