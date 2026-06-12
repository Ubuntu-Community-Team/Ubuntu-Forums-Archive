---
title: "Dell Precision 390 network card not connecting"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by beezum88@gmail.com on 2010-03-29
So I bought a used Dell Precision 390 Workstation and installed Ubuntu 9.04 on it.  Everything seems to work fine, except for the built-in network card.  Well, the graphics don't really work right, either, but I rather expected that, and I'll get to it later.  

Anyway, when I boot Ubuntu and try to get on the internet, it says I'm not connected.  When I open Network Tools, in the "Devices" tab, I get three Network device options: Loopback Interface, Ethernet Interface (eth0), and Unknown Interface (pan0).  When I click on the ethernet device option, it shows me the hardware address of the interface, that it has multicast enabled, and that it is "Active", but I get no IP address.

Is there something really stupid that I'm missing?  Do I need to do something special the first time I hook up an ethernet cable?  I don't seem to remember having to do that on other Ubuntu boxes.

Any help would be appreciated, but bear in mind that I know only enough about this stuff to get myself into trouble :-P

---

### Post by Iowan on 2010-03-30
Check (post, if possible) results of **sudo lshw -C network** - that *should* provide more information on your interfaces. **ifconfig -a** isll show the interfaces - whether active or not. I'm curious to see if the card gets **real** IP address - or a 169.255.X.X **avahi** (zeroconf) address or (as you reported) none at all...

---

### Post by beezum88@gmail.com on 2010-03-31
I booted the machine just now to implement your suggestion, and both my network issue and my graphics issues had fixed themselves.  I'm a little annoyed, now, to be honest.  I swear I tried rebooting it before.  Multiple times. ](*,)  The only difference between then and now is that the computer is now hooked up to my monitor, keyboard and mouse through my KVM switch instead of directly.

Oh well, thanks for your help.

---

### Post by Iowan on 2010-03-31
You're welcome... I guess...
Hope it *stays* fixed! [-o<

---

