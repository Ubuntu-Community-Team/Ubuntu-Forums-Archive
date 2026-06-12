---
title: "Default Microphone Won't Stay"
date: 2011-06-17
forum: Multimedia Software
---

### Post by AlexParky on 2011-06-17
Hi everyone,

I'm having a lot of trouble getting the default microphone to stay as the webcam microphone in 10.04 LTS. What happened at first is that there was the motherboard microphone and the webcam mic - despite selecting it, once the computer went to sleep or was switched off, it would return to motherboard input (i.e. no input). So, I wrote a script that would change it back to the webcam each time the computer started. It didn't work so well, and eventually I found I could just disable the motherboard input entirely, which I did. Now, my only option for input is the webcam, but everytime the computer sleeps, it wakes up with it unchecked - as though it would rather have no input than the webcam. I've racked my brains and the internet for 2 weeks trying to solve this - any suggestions?

Motherboard is an M4A88T-M/USB-3, 500GB Seagate HDD, 3.2GHz AMDx2.

I really appreciate it - it's for my mother, and I can't leave her fiddling around in sound preferences after I leave... I really want her to love linux.

---

### Post by lidex on 2011-06-18
Try this. Set your sound config as you need it then run this command to save mixer settings:
```
sudo alsactl store 0
```
No joy?
Open this file for editing:
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

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

