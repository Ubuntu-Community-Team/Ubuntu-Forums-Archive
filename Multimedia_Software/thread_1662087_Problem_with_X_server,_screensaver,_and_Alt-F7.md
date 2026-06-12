---
title: "Problem with X server, screensaver, and Alt-F7"
date: 2011-01-07
forum: Multimedia Software
---

### Post by rtechie on 2011-01-07
I've got my copy of Ubuntu 10.04-1 LTS running, and everything appears to work just fine except...

When  the screensaver kicks in, or the monitor is unplugged or goes to sleep,  the user is kicked to a console prompt on F1. If I try to switch back  using Alt-F7, the X session is apparently locked with a text display and  some gibberish at the bottom, but reports as still running. I can't  seem to kill it and I can't seem to start a new instance with startx. 

It  looks like the driver might be crashing when the screensaver kicks in  for some reason, but I can't find this reported in logs anywhere.

Help on this would really be appreciated.

---

### Post by BicyclerBoy on 2011-01-07
Have you read thru' the /var/log/Xorg.0.log  ??
What is the video hardware ?

dmesg

To restart X server
service gdm start


disable the screensaver
disable desktop effects until you get the video driver working right.

---

### Post by rtechie on 2011-01-12
It looks like the problem was that I was using slim. When I replaced that with lxdm it seemed to solve the problem. Screensaver doesn't seem to work anymore, but oh well.

---

