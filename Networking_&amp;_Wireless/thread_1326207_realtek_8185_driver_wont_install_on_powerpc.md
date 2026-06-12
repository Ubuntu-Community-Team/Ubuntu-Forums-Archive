---
title: "realtek 8185 driver wont install on powerpc"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by furminger on 2009-11-14
Hi, a newbie question. I have just installed Karmic Koala build onto my old macbook G4 powerpc which detects the realtek 8185 pci wireless card but i cannot get any driver to install. 

*-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0001:11:00.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=64 mingnt=32
       resources: ioport:1000(size=256) memory:88000000-880003ff

Apparently i cant use ndiswrapper as its powerpc and when i try to run sudo make on the latest realtek drivers i get the following error

error: ‘struct net_device’ has no member named ‘hard_start_xmit’

does anyone know of a driver that will compile and install?

help please!

---

### Post by furminger on 2009-11-14
having tried everything i could find over the last 8 hours and having reinstalled a couple of times i am no where nearer getting the card to work and cannot find anything that works. The instructions from [http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page) result in errors when followed, the new drivers from realtek are obviously not for powerpc devices. would another flavour work? ie Fedora for powerpc

---

