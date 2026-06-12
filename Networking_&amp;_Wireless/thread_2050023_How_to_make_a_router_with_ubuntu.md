---
title: "How to make a router with ubuntu"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by Dragonpoet on 2012-08-29
I want to block cerntain websites, but unforunitally my router won't allow me to. So, I was think about shutting down the wireless part of my router, hooking a machine loaded with Ubuntu server up that has a wireless card via eithernet, and have that machine act as my "router" to be able to block website not just for my main computer, but all devices that connect through the network and also to make it more secure. Is this possible? I am somewhat a newbie to Ubuntu, so I do apologize if I don't understand or I give a bad understanding. Thank you in advance for helping me and taking time to read this. Have a good day/night.

---

### Post by nativehound on 2012-08-29
Try Smoothwall, it's great. I used to use that back in the day before nats were cheap. On the ubuntu side, yes but it's not going to be ez.
I think smoothwall would be easier for a new user to get everything up and running.

gl

---

### Post by pqwoerituytrueiwoq on 2012-08-29
you could just use opendns, real easy to use it to filter Internet
you just have to set the dns server on your router
as long as the user does not know they can change there dns server to on your router something else on there computer it will work perfectly
if you have access to all the systems in your network you could use this trick
[http://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/](http://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/)

---

### Post by Dragonpoet on 2012-08-30
Would I be able to share a encrypted ntfs file drive throughout my network as well? And would I have to install in under Ubuntu desktop or server?

---

