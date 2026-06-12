---
title: "Ad-Hoc Wireless Network"
date: 2006-04-24
forum: Networking &amp; Wireless
---

### Post by priyaaank on 2006-04-24
Hi,

I have a laptop equipped with Intel Centrino and Wi-Fi. I wanted to create a Ad-Hoc network [peer-to-peer] with other similar laptop. I tried to assign static IP 192.168.132.4 and 192.168.132.14 and subnet of 255.255.255.0.
Also, created group with name "xyz".
The thing to note is that, one comp is running Windows XP and other is running Ubuntu. 
I am not sure, why they are not able to locate each other.
Would be grateful if someone could throw some light on it, or tell me, how could I do it, step by step, to enable file sharing; as thats the main concern here.

Also, is it possible to share internet connection though Ad-Hoc network. I mean, if one of the computer had Internet, could I share my internet connection with other one, wirelessly? 

Thanks in advance.

---

### Post by spanishwasabi on 2006-04-25
Did you (both!) put your cards into ad-hoc mode?

> sudo iwconfig eth0 mode Ad-Hoc

eth0, wlan0 or whatever your wireless card is in.

Enjoy,

G

---

