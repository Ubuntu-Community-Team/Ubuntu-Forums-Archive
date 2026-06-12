---
title: "Internet access just in some parts."
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by arian88 on 2012-05-19
Hi,
I have very strange problem.
For some week ago I installed Ubuntu 12.04 on one of my PCs.
I want to use it as server, with no keyboard/mouse or monitor.
I just use SSH and VNC for remote control and its enough.

So I installed SSH and VNC, and the PC are at my job.
I can connect with SSH and VNC with no problem, and everything works fine from my home.
(So I can get access to the Ubuntu from some other location)

But my problem is, the Ubuntu have no internet access!
I mean when I go to firefox, no internet! I cant use ping!
When I'm on SSH, and I try to ping some host, I don't get any response.

Ubuntu have internet access for VNC and SSH for outgoing connection
but when I try to use fireofx, ping, install some packages, NO INTERNET!

---

### Post by SleepWalkerX on 2012-05-20
That sounds very strange considering you needed internet access at your Ubuntu server at work in order to connect to it at all from your home computer..  :|

edit:  Ah, perhaps it is your dns issues in that screenshot.  Try adding 4.4.4.4 or 8.8.8.8 or the opendns addresses in your /etc/resolv.conf file.

---

### Post by arian88 on 2012-05-20
thanks SleepWalkerX.

I tried to use IP address instead of domain name! and it works.
So I change my DNS ip to OpenDNS (208.67.222.222)
and now I have internet access.

So the problem as you say was DNS.

---

