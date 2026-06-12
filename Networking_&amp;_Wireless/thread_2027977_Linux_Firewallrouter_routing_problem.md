---
title: "Linux Firewall/router routing problem"
date: 2012-07-17
forum: Networking &amp; Wireless
---

### Post by lantoeter on 2012-07-17
Hello,

i have a problem for a long time with linux routing. Perhaps somebody can help me. 
I dont get any help by search with google

I have 2*Windows 7 PCs and 2*Gentoo Linux Firewall/Router.
The Gentoo Router have both a ppp0 interface to the internet.
I made a image with visio to understand the situation.
The main Problem is to make a RDP Connection from Windows 7 PC 1 192.168.50.10 to Windows 7 PC 2 192.168.70.123.
The only way for this to work is when i use the command "route add 192.168.50.0 MASK 255.255.255.0 10.10.0.250" on the Windows 7 PC 2 as you can see in the image.

The question is why do i need to add that route to every PC in the 192.168.70.0/24 net so that the RDP work, although i have a coresponding route at the Gentoo Router 192.168.70.1 ?

can someone help me?
what did i do wrong?

best regards
LANToeter

---

