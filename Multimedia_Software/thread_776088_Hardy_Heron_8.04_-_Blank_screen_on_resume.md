---
title: "Hardy Heron 8.04 - Blank screen on resume"
date: 2008-04-30
forum: Multimedia Software
---

### Post by raoulteeuwen on 2008-04-30
I just upgraded my Travelmate 4001WLMi with Ati Mobility Radeon 9700 (ubuntu reports it as 9600 m10) from Gutsy to Hardy. I had Compiz on Gutsy (love it) as well as Cairo Dock. I ran into some problems with video (white screen), fiddled around switching between Ati open source driver and Ati proprietary, and most of the problems seem to have gone.

However: when my laptop goes into sleep-mode, and i press a key to resume/wake up, i see some activity, but the screen stays blank.

I found some similar issues getting resolved with nVidia-cards, but haven't been able to find a thread with similar problems and resolution for my Ati-card.

Anybody has a clue? Please let me know if you need me to supply more info! Thanks & kindest regards,

Raoul.

PS How Ubuntu reports card: "lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"

PS2 System / Administration / Hardware drivers reports the Ati accelerated Graphics drivers enabled, but not in use

---

### Post by macpointman on 2008-05-09
I have a very similar issue.  With the blank screen after startup.  I have fixed the issue I was having with my screen resolution.  My 6.10 was p[erfect am really interested in getting this up and running.

---

### Post by plucesiar on 2008-06-12
I get this problem as well.  My video card is Nvidia Geforce Go 6150.  After going into sleep mode, the monitor remains as a blank (black) screen and will not respond to any mouse, keyboard, etc input activity.  Everything else is still working fine (can log in, etc.)

Basically like this problem:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119901](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119901)

I'm very new to Linux, so I don't know what other information to provide. A look at my Hardware Drivers under System, Administration, shows under the Device Driver tab that "NVIDIA accelerated graphics driver (latest cards)" is enabled and is in use.

---

