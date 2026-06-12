---
title: "Remember sound settings"
date: 2010-05-26
forum: Multimedia Software
---

### Post by miggys on 2010-05-26
Using Ubuntu 10.04.  Between reboots, my volume/sound settings are all reset.  Is there a simple way for ubuntu to remember my settings so my earphones aren't set to 100% everytime?  

I have done 
```
sudo alsactl store
```
to store current settings and
```
sudo alsactl restore
```
to restore the settings, but this is not done automatically.  I realize I can do the two commands at shutdown and start up if I wish, but I feel like this is something that is probably available already somehow, I just don't know where.

---

### Post by miggys on 2010-06-01
BUMP

Just to get some responses...do other people's volume settings get reset between reboots?  It's happening on both my installs.

---

### Post by lidex on 2010-06-01
Try this. Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

---

### Post by miggys on 2010-06-02
Thanks lidex, but this did not work.  I also commented out the same line from the system.pa file in the same directory and it still did not work.

I am wondering if my problem is not as straightforward as I am letting on.  To get the sound to what I think is acceptable, I adjust some settings in alsamixer (specifically the headphone channel).  Maybe pulseaudio restores what it thinks needs restoring but is not aware of the headphone channel setting?

---

