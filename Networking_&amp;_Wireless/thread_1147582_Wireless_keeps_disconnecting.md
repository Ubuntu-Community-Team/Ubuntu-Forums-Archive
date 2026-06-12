---
title: "Wireless keeps disconnecting"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by netwarriorwy on 2009-05-03
Hi! I'm using a Intrepid Ibex Ubuntu with kernel 2.6.27-11. My laptop is a hp pavilion with a in-built wireless card iwl3945, after updating because i wass trying to upgrade to Jaunty...my upgrade process failed because somebody turned off my laptop in my house, the day after that i tried to work with my laptop with Intrepid but the wireless connection was awful, everytime i connected my laptop to the router after 1 or 2 minutes i had to connect again, this is very annoying, any help would be appreciated :(

---

### Post by netwarriorwy on 2009-05-05
Hi! After i tried everything i started to think it was my router, but using win xp was fine, it didnt disconnect me from the network. The problem started somehow trying to upgrade to jaunty. So i decided to do a fresh install from the alternate CD.

After installing everything, the same damn problem again!!!! It had to be something with ubuntu, then I checked up several forums and somewhere I found something about a ntp package.

I looked for that package in the system log and found a problem with a connection to [COLOR="Purple"]ntp.ubuntu.com[/COLOR]

Then i went to the [COLOR="Purple"]filesystem[/COLOR] and checked inside [COLOR="Purple"]/etc/network/if-up.d[/COLOR] and couldnt find that package.

So i decided to install it. Open a terminal and type the following

> sudo apt-get install ntp

Voila!!! Is working for me. I can see in the logs that sometimes its reconnecting but at least i dont lose the connection, and the reconnection is so fast that I dont feel the delay.:popcorn:

---

### Post by Michal77 on 2009-05-05
Hi,
I got the same problem, when I have came to Thailand. Any connection is very unstable here. (Before I never had such a problem). I lost connection after 1 or 2 minutes, but network-manager or wicd were showing that all is ok.

It seems that an install of ntp have solved problem. 
Thanks a lot.
:)

---

