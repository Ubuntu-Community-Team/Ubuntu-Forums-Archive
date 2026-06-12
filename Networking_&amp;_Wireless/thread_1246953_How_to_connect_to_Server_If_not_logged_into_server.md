---
title: "How to connect to Server If not logged into server"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by mrchisel_s on 2009-08-22
Hey I'm trying to use Remote Desktop Viewer To connect to my ubuntu server which works great if the server is logged in however if I restart my server I cannot connect to the server unless I manually go to the server and log in. Is there a way to get the vnc server to load before I type in my log in or a way to connect and log in remotely I'm completely new to linux a friend a work told me about it and now I'm hooked. I've only been using it for 2 weeks.

---

### Post by TwistedTripper on 2009-08-29
> **mrchisel_s said:**
> ....Is there a way to get the vnc server to load before I type in my log in or a way to connect and log in remotely.......

Configure the server to login automatically. Then when you reboot the server, you won't need to type in a username and password.

That's how I have mine set up. So once the Ubuntu server box is started I run ultravnc from my windows box and remote desktop into the Ubuntu file server.

To make Ubuntu login automatically go to System -> Administration -> Login Window and under the security tab tick the enable automatic login box and specify the user. (that's how it is for Hardy - other versions will probably be similar)

Cheers

TT

---

