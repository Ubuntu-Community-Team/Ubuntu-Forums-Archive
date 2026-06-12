---
title: "Wi-Fi MediaConnect PTA01 in VMWarePlayer"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by GlisGlis on 2011-01-11
Hi,
Info: Running guest WindowsXP in VMWare Player 3.1.3, host:Ubuntu  11.04 

I try to run Wi-Fi MediaConnect for my TV (Philips) with the PTA01/00 usb adapter in my TV. Network-connections with my router-TV router-Laptop are working, so I can  use my TV browsing internet.

To project my desktop's content to my TV, I configured  VMWareplayer with the Bridged Network Adapter activated (others won't  work) and in this way my Laptop sees my TV, but my TV doesn't find my Laptop. 
I tried several settings, for my router as well, but I can't succeed. 

Any ideas? :confused:

Henk

---

### Post by PatchesTheCaveman on 2011-01-11
Many Philips TVs support streaming videos via UPnP.  This will allow you to use a native Linux UPnP server such as MediaTomb without fussing with the virtual machine.  Check your television's documentation to see if it supports this feature.

---

### Post by GlisGlis on 2011-01-17
Found out in [VMWareplayer] WindowsXP audiosettings must be WFMCVAD :p Projection started.

Still can't use MediaTomb. Didn't get reply from Philips. Working on it.:rolleyes:

---

### Post by Bazon on 2011-01-25
Mediatomb works for me. Make sure you allowed ui in the mediatomb configuration file /etc/mediatomb/config.xml , then restart medaitomb 
sudo /etc/init.d/mediatomb restart 
and then control mediatomb over the webinterface via [http://localhost:49152](http://localhost:49152) .

But still, this isn't the same as mediaconnect unfortunately.

---

