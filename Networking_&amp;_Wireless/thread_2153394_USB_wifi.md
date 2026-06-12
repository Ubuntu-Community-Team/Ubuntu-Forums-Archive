---
title: "USB wifi"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by rickyhj2002 on 2013-06-10
I am an average Linux user. I installed Ubuntu 10.4 on my Everex cloudbook and it runs great.  My internal wifi stopped working. I opted to a USB adapter. When I plug it in, nothing happens. I have searched this forum and found similar problems but not sure how to fix the issue still.will any of the adapters be easier to get working? I even have the disk to go with this adapter and it says windows and Linux on it but don't know how to install it.I'm really not as dumb add I sound, just loving Linux.

---

### Post by Bucky Ball on 2013-06-10
*Thread moved to **Networking & Wireless**.*

Firstly, 10.04 LTS reached end-of-life at the end of April. Don't go there. You will get no updates, and importantly, no security updates;  a risk if this machine is online. 

I would install the current LTS (long term support release) 12.04 LTS, supported until April 2017 and report back. 

You see, to fix this problem I would say put the USB dongle in, run an update and look in Additional Drivers and/or reboot, but an update will make no difference as there is nothing to update (although third party repos, if you have any, will update as per normal).

Immediately after you boot, put the dongle in then open a terminal and run 'dmesg'. At the bottom, what does it say about inserting the dongle? Does it recognise it? Post the exact message you are getting.

PS: 12.04 LTS uses Unity desktop environment, which you might not like, but there are plenty of alternatives. I use Xubuntu but before that used its desktop environment, xfce, with Ubuntu because I don't go for Unity, myself. Good luck.

PPS: You will have more luck with thread titles that give some clue about your exact problem and by including as much info as you can muster. You have not mentioned the dongle you are trying to get up ...

Plug it in and run:

```
sudo lshw -C network
```

You have not bothered to try fix the internal card? Anyhow, that might start working again with a supported release and updates.

---

