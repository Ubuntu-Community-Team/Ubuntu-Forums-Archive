---
title: "Power Managementmode: All packets recieved problem"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by goemonburo on 2011-07-30
I just got a Dell Latitude 2120 with Ubuntu 10.10 preinstalled.  Not particularly wanting to upgrade, but right out of the box I've noticed that there's a HUGE speed drop in the wireless when it's on battery power.

Running iwconfig shows that "Power Managementmode: All packets received" is on when on battery power.  It's "off" when I plug in the A/C.  My hunch is that this is causing the problem and I'm not needing to squeeze every ounce of life out of the battery.  

How can I simply make sure that this Power Management is OFF when I'm on battery power?

I've tried a few things I've seen on the web.  One, I added a dummy "/etc/pm/power.d/wireless" file.  Then I edited it to include "/sbin/iwconfig eth1 power off" Still no dice.  Then I edited the /usr/lib/pm-utils/power.d/wireless" file and changed all the "power on"s to "power off"s (matching what I thought was A/C configuration).  STILL no dice.  Finally I've added "/sbin/iwconfig power off" to my /etc/rc.local file.  Sure enough:  still got nothing.

Surely this can't be totally impossible...in fact, I'm sure it's easy but am guessing I'm barking up the wrong tree.  I did notice that it's using Broadcom proprietary drivers...are these causing the problem?  Is this a known flaw and the only solution is to upgrade?  (Which I hesitate to do since it might break other things, like the webcam or sound...)

Ideally, some power management guru out there knows what's going on here.  I'd love to see this work.  For now, the solution is just to stay near A/C power, but that kind of defeats the purpose of a netbook, right?  :-)

(This option turns off if I manually type "sudo /sbin/iwconfig eth1 power off" at the command line...so the question is really just where to put this line so that it happens automatically.  Presumably I can type "sudo /sbin/iwconfig eth1 power on" when I need to eek out every ounce of battery life...)

Any help would be greatly appreciated.  Thank you!

---

### Post by wildmanne39 on 2011-07-30
Hi, try this it will turn power management off.
```
sudo iwconfig wlan0 power off
```
Let us know if it works of it does please use thread tools and mark this thread solved.
Thank you

---

### Post by goemonburo on 2011-07-30
Like I said in the original post, that works (my system has eth1, not wlan0, but it's the same thing).  But I don't want to have to manually type that each and every time I'm not connected to AC power.

How do I do that automatically?  It seems like there should be some Preferences (or a config file) that when properly adjusted will keep the wifi power settings the same for both battery and AC power.

Thanks!

---

### Post by goemonburo on 2011-08-03
Bump?

---

