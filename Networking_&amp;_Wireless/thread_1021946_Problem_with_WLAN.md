---
title: "Problem with WLAN"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by Blueball32 on 2008-12-26
Hey, I'm new to Ubuntu and I have already managed to set everything up, but I'm encountering troubles with my WLAN(-driver?).

The whole system works perfect except for the Nvidia Beta driver(but thats not the point here) and the WLAN. With activated WLAN my Notebook chrashs every 10 Minutes (two blinking symbols - Kernel Panic) so I thought about a driver update, but I don't know where to get and how to install one, or...well do you have an idea how to solve this?? :(

Blue

P.S.: I should mention that networking works because right now I'm using Ethernet (and used it yesterday hours without any prob)

---

### Post by theozzlives on 2008-12-26
Try going to the MFG. website  and download the Windows driver for your  card, then use NDISWrapper  to  make it work in Linux.

---

### Post by Blueball32 on 2008-12-26
Thanks for the tip, but I'm stuck... :(

How do I extract those exe.files, cause I need the .inf and .sys files within those exes. I tried unshield, 7zip and cabextract and nothing worked! 
Can someone help me with this?
Blue

---

### Post by husky55 on 2008-12-26
> **Blueball32 said:**
> Thanks for the tip, but I'm stuck... :(

How do I extract those exe.files, cause I need the .inf and .sys files within those exes. I tried unshield, 7zip and cabextract and nothing worked! 
Can someone help me with this?
Blue

You could go to the windows dir   and look for the sub dir INF and look for   your driver in windows.

---

### Post by Blueball32 on 2008-12-26
Nice idea, but how do I find that special WLAN driver among those 1000 other driver files...? 

I'm also not sure if ndiswrapper is able to convert my Vista driver for Ubuntu. In the readme only XP is mentioned... :(

---

