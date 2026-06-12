---
title: "Mercury TV card support?"
date: 2006-08-14
forum: Multimedia &amp; Video
---

### Post by derby007 on 2006-08-14
I have a Mercury TV card (7130) with Phillips 7134 chipset onboard, i've downloaded TVTime and got it to open using this command at the prompt : 'tvtime --inputwidth=400'. I then get a 'black' screen. Note: it comes up with an error if i try 'tvtime'. Also: when i use 'dmesg': i see "board: UNKNOWN/GENERIC [card=0,autodetected]" as my card, along with an eeprom o/p:  is this a problem? I probably should set it to a tuner, right? But i don't see my Mercury card listed in the 'Cardlist'. Also...how do I to tune it. My input into the card is from my Sky satelllite "EXT2" o/p, ie. the o/p that can feed to another TV. Anyone got any ideas...:?:

---

### Post by liarsenic on 2007-04-30
Easy fix.

I use OpenSuSE 10.2 so it's maybe different for ubuntu. If the commands i use arent the same, find the ones that ubuntu uses and it should work. Also, I use the boot.local file in /etc/init.d to run the commands at startup, if its different in ubuntu, find the file you usually put stuff for startup and edit it with these lines.

in boot.local:

[I]rmmod saa7134
modprobe saa7134 card=3 tuner=39[/I]

Save the file, reboot, fire it up.

---

