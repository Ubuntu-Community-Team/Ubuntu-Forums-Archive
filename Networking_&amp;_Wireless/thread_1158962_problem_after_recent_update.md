---
title: "problem after recent update"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by dikkie on 2009-05-14
Hi, I would like to apologise first of all if this has been asked already. I'm kinda new to Ubuntu and I have updated my system and in the update was a linux kernel, this has stopped me from connecting to any wireless internet... as a matter of fact the network thingy that allows you to enable or disable connections no longer gives any option for enabling wireless. I have an Atheros AR5BXB63 card and an Atheros 802.11 Lan card driver and I'm running on Ubuntu 8.10.

So I have an idea about what the problem is, but I am unsure how to fix it, or for that matter what to look for

I typed in iwconfig into a terminal and was told that there are no wireless extensions.
The Lan Driver says that it is working and in use.

Please help

---

### Post by superprash2003 on 2009-05-14
do you get any error like " device is unmanaged" ?

---

### Post by bluestreek on 2009-05-14
Try doing:

sudo apt-get install linux-backports-modules-intrepid

Once you have it showing up in iwconfig I think I have a command which will fix it.

---

### Post by dikkie on 2009-05-14
After doing what you asked I got this reply from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

tun0      no wireless extensions

No change

---

