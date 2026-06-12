---
title: "can't use wireless after update"
date: 2013-01-25
forum: Networking &amp; Wireless
---

### Post by krisehrlich on 2013-01-25
I've installed Ubuntu 12.04 on a new Compaq cq58 laptop.  After installing Ubuntu wifi dind't work, but following instructions on  the forum I could install the drivers and make it work....now after  updating wireless stopped working...I don't know what to do now...
  
~$ sudo rfkill list all

 0: hp-wifi: 
Wireless LAN     
Soft blocked: no     
Hard blocked: no 

1: hp-bluetooth: 
Bluetooth     Soft blocked: no     
Hard blocked: no   

~$ lspci -nn | grep 0280 

04:00.0 Network controller [0280]: Ralink corp. Device [1814:3290]

---

### Post by Bucky Ball on 2013-01-25
[I]Thread moved to [B]Networking & Wireless

[/B][/I] You probably need to follow the same instructions and procedure as you did to install the drivers last time.

---

### Post by krisehrlich on 2013-01-25
> **Bucky Ball said:**
> [I]Thread moved to [B]Networking & Wireless

[/B][/I] You probably need to follow the same instructions and procedure as you did to install the drivers last time.
the problem is its a while ago and i can neither remember how i did it, nor find the instructions on how to do it

---

