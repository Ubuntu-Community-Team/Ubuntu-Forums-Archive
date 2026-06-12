---
title: "Wifi on Dell Inspiron 9400 - Intel PRO/Wireless 3945"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by Jabz.biz on 2009-02-19
Hi, 

I'm on this problem for several hours now...I think I need some help quick. 
I have installed Ubuntu Hardy LTS on a 32bit Dell Inspiron 9400. Everything but the Wifi works fine. 

Wifi Networks are found, but connecting to them is the problem. I'm constantly asked for the WEP Key. I enter it but can not connect. The Wifi has an Intel PRO/Wireless 3945 Dual Band 802.11a/g 54Mbps Wireless Mini Card

uname -r gives back: 2.6.24-23-generic
ndiswrapper -l gives back: currently not installed

When I try to install ndiswrapper: 0 updated, removed, new
So I've installed ndisgtk (GUI for ndiswrapper) and the ndiswrapper utils 1.9

When I try to open ndisgtk (System > Administration > Windows Wireless Drivers) it crashes/ opens and closes itself immediately.


Here I am,...offline. :) Does anybody have some advice for me? Any ideas?

---

### Post by stevena0 on 2009-02-19
This may or may not be helpful, but I've had a similar problem before.

In my case the problem was the signal not being strong enough, or too much interference. It's still an intermitent problem for me when my wireless signal isn't very strong.

Try these as a start:

 - Move really close to your router and try again.
 - Change the channel on your router, and change the mode to g only, instead of b&g or auto. (This is what fixed it for me).

Post back and let us know how these go.

---

### Post by Jabz.biz on 2009-02-19
Hi, thanks for your reply. 

I'm pretty sure now, that this is a driver issue. See my post above, I have just added a few things. My latest problem is, that ndisgtk crashes when I try to open it for installing the needed driver.

---

### Post by rlgc79 on 2009-04-02
I have the same problem here. There are days that I cannot connect to the Network with Ubuntu. Everything works well when I switch to Windows, so I believe it's a driver issue.

---

### Post by freonchill on 2009-04-02
what kernel are you running?

---

### Post by rlgc79 on 2009-04-04
2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

---

