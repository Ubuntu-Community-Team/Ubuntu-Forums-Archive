---
title: "Sony PCG-V505BX"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by snowcraig on 2009-05-28
Does anyone else here have this laptop?  I have Ubuntu installed, but cannot connect to my home wireless network when I have it set to WPA security.  It successfully detects the network, but when I try to connect it doesn't list WPA as an option.  I can plug in my USB WIFI stick and then connect to WPA, but not with the internal hardware in my laptop.  I can also switch the network to WEP and connect with the interal wireless card alone, but I don't really want to do that.  Does anyone here have a suggestion for me?

Thanks
Craig

---

### Post by snowcraig on 2009-05-29
I believe this is the actual wireless hardware that comes with the computer:

LAN Express AS-IEEE 802.11 miniPCI Adapter


Can anyone help?  I want to keep ubuntu, but if I can't get the WPA to work I am going to have to go back to windows.  :(

---

### Post by snowcraig on 2009-05-31
Also,, the laptop can get WPA when running Windows XP.

---

### Post by snowcraig on 2009-06-01
Bump...

---

### Post by t0mppa on 2009-06-01
Open up a terminal, run **lshw -C network** and post back with the output to get an idea what chipset/card you really have and which drivers you're using. Hard to give any advice without knowing what we're dealing with here.

---

### Post by snowcraig on 2009-06-01
Here is what I came up with:


*-network:0             
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 01
       serial: 00:02:8a:94:be:87
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.5.6 latency=64 module=orinoco_pci multicast=yes wireless=IEEE 802.11b
  *-network:1
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 08:00:46:ad:1d:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1c:df:78:1f:87
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.2.3 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 9a:a0:51:05:54:4e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


Is this all that you needed?

---

### Post by t0mppa on 2009-06-01
Enough to realize that it's beyond my knowhow. Never set up a prism card, so can't help you with that more than guess what might be wrong. For instance, some drivers simply don't support WPA and in those cases you have to try different drivers. But like I said, I know nothing about Prism chipset configurations, so unfortunately cannot offer any help with it.

There are others on the forums who know how to configure them though, so just be patient and someone will pick it up.

---

### Post by snowcraig on 2009-06-02
I was figuring I would have to try new drivers, but I have no idea how to install drivers in Ubuntu.

---

### Post by desnaike on 2009-07-05
Sorry for the late reply The wifi card in our sony only supports WEP.

---

### Post by snowcraig on 2009-12-11
> **desnaike said:**
> Sorry for the late reply The wifi card in our sony only supports WEP.


Are you sure, I was pretty sure when I had XP on this computer it supported WPA?

---

### Post by desnaike on 2010-01-01
Yes I am sure.

---

