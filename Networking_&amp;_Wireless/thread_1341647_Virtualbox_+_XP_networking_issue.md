---
title: "Virtualbox + XP networking issue"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by Julolidine on 2009-11-29
Hi,

I install 9.10 on my wife's laptop.  This is an old inspiron 5100 from Dell.  Anyways, I've installed Virtualbox + XP on a couple machines in the past, and never had problems with the networking.  Now I do. 

In the Virtualbox settings, the network adapters are enabled and are PCnet-FAST III, attached to NAT.  I've tried the different combinations (ie selecting the different things that it could be attached to), and gone back and forth between the wireless and the wired connection.  

In Windows, nothing is listed under network connections, and starting the network setup wizard stops because it says "no network hardware detected".  

This is vanilla Windows XP that came with the computer (before SP2).  I also tried reinstalling the windows once, and its more or less the same.   

Any ideas?   

Versions are 9.10 ubuntu, new kernel, 3.0.12 for vbox.  

Everything runs fine - usb, sound, etc.

---

### Post by jacobs444 on 2009-11-29
try enabling a second adapter in the settings for the VM. I have had problems with this before, hope it helps. also, if you haven't done so you may want to install guest additions. While in the VM press the right hand ctrl+d

---

