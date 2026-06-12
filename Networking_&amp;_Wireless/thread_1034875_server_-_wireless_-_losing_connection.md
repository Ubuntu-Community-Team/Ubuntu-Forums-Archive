---
title: "server - wireless - losing connection"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by anewguy on 2009-01-09
I have I guess a little strange set up:  my PC for work in Windows XP Pro and is required to be hard-wired, so I ran a cable to one of the ports on my wireless router.  I also have a simple Ubuntu 8.10 server box, sharing a hard disk to the network.  The server is not hard wired to the router but instead uses a Belkin FSD7050 v4000 USB wireless adaptor (Ubuntu installed a driver for it automatically).

My server seems to sort of randomly lose its wireless connection to the router (I'm using a static IP on the server).  Switching the USB cable to another USB port on the server box makes no difference - I have to reboot the server.

I know it's possible my or one of my neighbors phones might be interfering with the wireless, so I'm wondering if there is something I am missing to tell the server to reconnect the wireless after a disconnect.  Right now it acts like once it loses its connection to the router it never tries to reconnect.

Thanks in advance!

Dave :)

---

### Post by anewguy on 2009-01-12
Okay, it appears the driver is apparently shutting down the device or something.  If I unplug the adapter from it's stand, wait a couple of minutes, then plug it back in the wireless is back.  So, is there a way in a shell script to check the status of the wireless, and, if down, restart it.  If so, could I add  this to cron or something to run every 15 minutes or so and keep my wireless up?

Thanks in advance!

Dave :)

---

### Post by anewguy on 2009-01-20
Bumping up in case someone has some ideas.  Basically, via a script (or program if I need to write one), I want to check the status of the wireless connection, and if it is down I want to restart it.  Is there a way to build this in to use ifup or ifdown or some such thing?  Once working, I'll add it to cron so it cycles every few minutes.

Any help would be greatly appreciated!

Thanks in advance!

Dave :)

---

