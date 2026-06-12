---
title: "Can't connect to WPA2-Personal after update to Lucid Lynx"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by Zalastax on 2010-06-24
I updated to the latest version of Ubuntu and before I could connect to the network "krafft" that is a WPA2-Personal protected network.
If I go into Windows and change security to none I can connect with Ubuntu, but not when it's protected.
After a bit of time logged in without network a dialogue pops up and looks almost like this :
[IMG]http://planetkris.com/misc/Screenshot-Wireless%20Network%20Authentication%20Required.png[/IMG]



but "Focus" is replaced with "krafft" and the password is something else.
I know that the password is right and the network worked perfectly before update.


I got an USB wireless network receiver from D-Link and the chipste is ralink rt2870.
In the previous Ubuntu distribution you had to write "blacklist rt2800usb" in /etc/modprobe.d/blacklist.conf but it won't work with or without that blacklist.

When I updated I saw some message about the network manager(at least I think so) so maybe the problem is in that.

---

### Post by Zalastax on 2010-06-25
bump

---

### Post by Zalastax on 2010-06-26
Noone can solve this?

---

### Post by Talon2 on 2010-06-26
There may be some information here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549801)

You might try installing this:

linux-backports-modules-wireless-lucid-generic

---

### Post by Zalastax on 2010-07-19
I'm sorry but it didn't work(been on vacation that's why the long time till answer).
Tried everything I could find in the link and installed the package but nope.

---

