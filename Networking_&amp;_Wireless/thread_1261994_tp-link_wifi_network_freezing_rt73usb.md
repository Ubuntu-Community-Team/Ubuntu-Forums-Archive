---
title: "tp-link wifi network freezing rt73usb"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by xopher_mc on 2009-09-09
Hi I have a problem that is slightly wierd. I am using a wn321g tp-link usb stick on jaunty 64bit.

lsusb reading 

148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

The problem I have is that the network is working but then freezes for a couple of seconds. I.e cannot load network. When I ping it is replied to but with a ridiculous time. 

I understand that there are two wifi adaptor (with different chipsets) with this usb id. 

I tried blacklisting the the rt2500 module so it only used the rt73usb module. I thought it had worked but then the network froze again. Also installed the backports modules to see if a newer version of the module would get rid of the problem! No luck. 
:(

---

