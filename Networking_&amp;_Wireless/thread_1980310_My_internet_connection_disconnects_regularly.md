---
title: "My internet connection disconnects regularly"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by johnpeter1 on 2012-05-15
Dear members...I'm new to Ubuntu and installed ubuntu free edition, the problem is, in regular time interval(like 15 mins) the internet disconnects automatically and if only I restart it connects back. How to fix this issue or why this happens ? Please clarify me.

---

### Post by roelforg on 2012-05-15
First of all: There's no "paid" ubuntu version (unless you count the hosting canonical offers).
Are you on wireless?
If so, try using a cable directly to the router and report if the problem still exists when on the cable.
Cause i'm suspecting there's something with the WiFi signal.

---

### Post by squilookle on 2012-05-15
Hi johnpeter, 

Some more information would be helpful, because with internet connections there are an awful lot of things that can cause problems.  

What router/modem are you using? 

Do you have any other computers or connected devices in the house and, if so, do they have the same issue? Are you dual booting with Windows and, if so, does Windows have the same issue? 

I assume you are using wireless but your post actually does not say: are you able to connect using a wired connection temporarily, just to see if that fixes the issue? 

When did the problems start - just after installing Ubuntu or later? 

The problem *could* lie with Ubuntu, and if you have a Windows installation that does not have the same problem, that is likely the case. 

However, it could also be that you just need to reset your modem/router and everything will be alright (I have to do this about once a week). It could even be that there is something interfering with the signal, or that you are too far away from the router.

---

### Post by mörgæs on 2012-05-15
Moved to the network forum.

---

### Post by brijabasi on 2012-05-15
Hi all!

I have the same problem, I thought it would be better if I post it here than to start a new thread. I'm using WiFi on Ubuntu 12.04 (upgraded from 11.04 thru 11.10), but internet connection regularly disappears. Typical example: I turn on my laptop and connection cannot be established, I have to either do "sudo restart network-manager" or if that (usually) fails - to open "sudo gedit /etc/network/interfaces" and to change eth0 to wlan0, then internet appears, but after some time again vanishes and appears either after restart or after changing back wlan0 to eth0. The problem is with 12.04 since I have no WiFi issues on another PC with 10.04 LTS on it. 

Many thanks in advance.

---

