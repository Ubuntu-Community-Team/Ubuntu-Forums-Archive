---
title: "enable wireless at boot cause's everything to crash and freeze."
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Maciejl06 on 2009-12-06
Over the past week, i have been facing an unbearably frustrating problem; it seems that every time I boot my laptop up, it freezes within seconds not allowing me to click a single thing, I'm lucky if i get to see the wallpaper before the freeze...

i know it has something to do with the wireless internet because, if the wireless switch is disabled at time of boot, everything works fine, i can later than turn it on once everything is loaded, and it works problem free; that is until i try switching connection, or lose the connection temporarily. 

The freeze affects my whole desktop, i cant move my mouse, click, keyboard doesn't work, and everything on the desktop remains motion less. you can hear the hardrive running and lights are blinking within the first 4 seconds of freeze time.

I am running: ubuntu 9.10 
my wirless card: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
My computer: Acer aspire one 

in the meantime before this problem can be solved , i was wondering if there is a way to disable wireless from starting when a user logs on in ubuntu without having to physically turn off the switch.

---

### Post by Maciejl06 on 2009-12-09
well, i fixed the problem; it came to the point where my wireless just never functioned properly, so i installed a new networking client, wicd. But when it installed it removed my previous manager, and wicd didn't seem to get a nice install, so i uninstalled it... this left me with nothing, so I couldn't go on-line through wireless or Ethernet. 

I just booted ubuntu into recovery mode, chose the option with networking, and typed.
```
apt-get install network-manager
``` with my Ethernet cable plugged in, this resolved my issue.

---

