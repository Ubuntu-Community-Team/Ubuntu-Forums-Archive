---
title: "Hang on checking battery state..."
date: 2011-06-30
forum: Multimedia Software
---

### Post by neuralzen on 2011-06-30
Hi everyone, hopefully someone here may be able to help me regain my sanity, as ubuntu 11.04, much like Cthulhu, is eating it.

Anyway, my system hard locked while I was messing around with an N64 emulator, and I was forced to power it off. When it booted back up it keeps trying to go into low graphics mode, but just hangs on "checking battery state" if I try to do so, or just about anything else for that matter.

I've been hitting my head on this for the past three hours, and have tried uninstalling my nvidia drivers (running a nvidia 8800GTS), reinstalling gdm, purging compiz and other drivers and reinstalling them, all to no avail, and nothing ever changes on boot; it is always the same behavior. I tried resetting unity with "unity --reset" but got a GError error. I can boot into Win7 just fine, as well as the Ubuntu LiveCD, but can seem to repair this issue. I've also tried removing or altering the xorg.conf file, but I understand that 11.04 pretty much doesn't use it anymore

Any insight would be greatly appreciated!

---

### Post by Yellow Pasque on 2011-07-01
Look at your /var/log/Xorg.0.log (because it's hanging on trying to start X).

---

### Post by d0npirul0 on 2011-07-01
sudo aptitude purge all drivers(you know)
sudo aptitude purge libgl1-mesa-dri xserver-common-core

then:

sudo aptitude install xserver-xorg
sudo dpkg-reconfigure xserver-xorg



startx OR reboot (I had to restart)


I have the same problem at the same time.

good luck

---

### Post by thiagoxkim on 2011-07-01
I'm using Gnome 3 here, my video is an Intel 950.

when I changed gdm login option "AutomaticLoginEnabled" to True in /etc/gdm/custom.conf, this problem appear here.

I just turn back to False, and fixed...

---

### Post by neuralzen on 2011-07-03
Temüjin - I checked out the log files,but didn't seen anything that was very helpful. I'll post it here a bit later when I can get to the log file again.

d0npirul0 - I tried your suggestion, but no love. Just got the same thing.

thiagoxkim - I didn't mess with the gdm config, but I'll give your suggestion a shot and post back!

Thanks for the ideas guys...

---

### Post by swaroopbasagare on 2011-10-03
Try following steps ;
1. sudo apt-get remove --purge
2. sudo apt-get remove --purge libgl1-mesa-dri
3. sudo apt-get install xserver-xorg
4. sudo dpkg-reconfigure xserver-xorg
5.startx or reboot your machine

I hope this should work as it worked for me .. :)

---

