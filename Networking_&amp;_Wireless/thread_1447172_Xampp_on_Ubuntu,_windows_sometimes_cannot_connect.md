---
title: "Xampp on Ubuntu, windows *sometimes* cannot connect"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Elijah on 2010-04-05
Hi, 

This is an odd issue... I have an Ubuntu latest box that runs as a server for my xampp. And then an old windows laptop to connect with, this is for web development purposes. 

When I boot up windows I try and access the local ip of the server = it works. 
But after awhile.. maybe a few mins or an hour windows cannot connect anymore of Ubuntu, I always get "Internet explorer cannot display the webpage" error. I tried ping and it would not work, I'm quite sure the IP did not change at all. 
I reboot and try again, it works. I reboot again to test, it doesn't work. 


I don't get it, =/ Ubuntu doesn't have any form of firewall, just the default settings. Both could use the internet but oftentimes fail for local networking... 

Anybody has an idea what could be the problem here?

---

### Post by mizar001 on 2010-04-05
Is your ubuntu virtualized or in some other machine connected to the network ?

In the first case you should control with some virtual software console the network status from inside the ubuntu.

In case of another machine you should enter the router and try to ping ubuntu machine from here.

Furthermore the firewall can be in windows, and i assure it can generate most of unexpected and odd problems :D

---

### Post by Elijah on 2010-04-05
No, I don't use any virtual software.

Hmm... I tried to ping using both the server and router when the windows box had it's hiccups... the results where that there are some packet loss. Both are using wireless. 

It could be my router.. but then again the internet for both is perfect, the problem is the local network that fails once in awhile =/ hmm..


Update: ok, another odd thing.. loading of the localhost webpage fails but it can still ping.. I'm wondering now if this is a problem with my xampp or my router or both..

---

