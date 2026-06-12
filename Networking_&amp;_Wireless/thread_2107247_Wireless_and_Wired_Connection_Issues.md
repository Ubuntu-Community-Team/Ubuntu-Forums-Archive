---
title: "Wireless and Wired Connection Issues"
date: 2013-01-21
forum: Networking &amp; Wireless
---

### Post by dolphin194 on 2013-01-21
I have an MPC TransPort T2300 with Xubuntu 12.04 LTS installed. Since the laptop is made to run Windows XP and nothing else, I decided to try Ubuntu out on it. It works great...except for these networking problems.


[SIZE=3]**_*Wireless Issue*_**[/SIZE]
Basically what happens is I connect to the wireless network perfectly fine. It says I am connected, however all my applications do not connect to their servers.

For example, Firefox times out before it loads the web page, and Skype has the 'connecting' icon up all the time.

When I list my PCI devices, it comes up that I have this card:  
**Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection**
Wired connections work perfectly fine on this laptop.

[SIZE=3]**_*Wired Issue*_**[/SIZE]
Now for the wired connection problem. When I am connected to a wired network via internet, Firefox stops going to web pages after about 5 minutes. Firefox keeps saying that it is waiting for the server to send data. In order for me to get Firefox to load pages again, I have to re-connect my Ethernet.

I would really hate going back to Windows XP on this laptop.

---

### Post by Nr90 on 2013-01-21
Intel's driver has had a long bug when it comes to using wireless-N.

This page gives some suggestions you could try:
[http://askubuntu.com/questions/66873/wireless-2915abg-not-working-on-a-dell-xps-m140](http://askubuntu.com/questions/66873/wireless-2915abg-not-working-on-a-dell-xps-m140)

---

### Post by dolphin194 on 2013-02-01
I updated the machine to Xubuntu 12.10, and that stopped the problem for a while, but the same thing is happening again.

What I noticed while I browse the web, with any web browser, it times out some of the time. It doesn't matter whether I am connected to wired OR wireless. 

> **Nr90 said:**
> Intel's driver has had a long bug when it comes to using wireless-N.
It doesn't only happen on wireless, it happens on a wired connection too.

---

### Post by dolphin194 on 2013-02-06
Bump

---

### Post by howefield on 2013-02-06
Thread moved to the "*Networking & Wireless*" forum.

---

