---
title: "Ubuntu takes ages to start wifi"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by mariano_de on 2009-05-23
hello out there,

I am having a little problem with my ubuntu 9.04 jaunty, it takes around 1 to 2 minutes to start the wifi. Also when I wake up my notebook from suspension takes the same time till it connects again.

I never had the problem with any previous version of ubuntu.

my wcard is a Intel 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile

thank you!

---

### Post by superprash2003 on 2009-05-24
i'm having a similar issue, only when i resume the laptop from sleep mode . when i boot it works fine.. since its just a matter of 1 minute or so , i've just ignored it..

---

### Post by fak3r on 2009-07-21
I'm having this same issue on my Dell Mini 9 - my previous install of Ubuntu on my other Dell laptop would grab the wifi connection almost immediately, but this seems to wait around for quite some time.  I've been grepping around in /etc for some if-net-up scripts, but haven't found anything that tells nm-applet to reconnect (assume there's a timing config for this somewhere)

Hoping others have seen this, otherwise I'll post if I find a solution.

---

