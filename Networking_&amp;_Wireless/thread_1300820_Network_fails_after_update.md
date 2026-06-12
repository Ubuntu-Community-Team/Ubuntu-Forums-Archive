---
title: "Network fails after update"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by GGTutor on 2009-10-25
I posted this on installation thread but thought it might be more suitable here.

I am new to linux and have been trying to install 9.04 for the last 3 days, I am close to giving up now.](*,) I got everything working on the live cd and then installed to a separate drive to dual boot with xp. Everything worked fine:P. I then updated and found that I had no network connection, so I have spent ages trying to find solutions, no luck as my ASUS P5Q-E seems compatible and nobody else seems to have the same problem.

So, I went back to the live CD and found that this now also cannot connect, when it could before:confused:. Anyway, to cut a long story short and after reinstalling several times, I think I have found the problem.

After updating I am offered two kernels to boot from 2.6.28.16 or 2.6.28.11 (the one on live cd) If I boot into 2.6.28.16 I get this error on a black screen when shutting down

>nm-system-settings: SCPlugin-ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_
>nm-system-settings: SCPlugin-ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_


and have to press the power button to reset. On rebooting I can no longer get a network, this includes from the live cd. If I boot into 2.6.28.11 (without having booted into 2.6.28.16), I get a network but the system is now incredibly slow and eventually crashes.:(


I am afraid with my limited knowledge of linux I haven't a clue where to start now. Can anyone help me, I'd really like to try ubuntu out even though my first steps haven't been encouraging.


I found this page that makes me think it is a bug, am I right?

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/357578](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/357578)


Cheers

---

### Post by GGTutor on 2009-10-25
Can someone help me by suggesting what this error means

>nm-system-settings: SCPlugin-ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_
>nm-system-settings: SCPlugin-ifupdown: devices removed (udi: /org/freedesktop/Hal/devices/net_



as I have no idea and therefore don't know what to do next to install ubuntu.

PLEASE:(

---

