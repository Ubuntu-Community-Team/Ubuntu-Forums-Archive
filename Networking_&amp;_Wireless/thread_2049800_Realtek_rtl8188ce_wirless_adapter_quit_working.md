---
title: "Realtek rtl8188ce wirless adapter quit working"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by bjeff2010 on 2012-08-29
Ok, yesterday when I booted my laptop it would not let me connect to the internet. It could "see" the wireless signal from my router and attempt to connect but it would never fully connect and continued to repeatedly ask for my password. Adapter is the realtek rtl 8188ce. I was running 12.04 32 bit.

This problem is "fixed" at the moment since I was upgrading OS. I used a USB Wireless Adapter and was able to download and update to 12.04 64 bit.

I was wondering if there is a known cause and/or fix for this in case it happens again.

Thanks in advance for the help.

SOLVED: It was the router that had gone bad...no issues with wireless card.

---

### Post by cblanquer on 2012-11-06
Hello,

I made a fresh install of Ubuntu 12.04LTS 64b on 2012-11-04. 
My computer uses the same WiFi adapter but the connections is not usable: absolutely unstable as drops after some seconds and is not able to reconnect (WPA key => asks for the password again and again).

Does it sound similar to the issue you had? I have 5 other computers with different OS flavours and onl the latest is creating problems.
THX

(* I just found out that bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/902557) deals with that and apparently the new drivers form RealTek work -  I saw they released a new version recently. So let's build up the whole stuff *)

---

