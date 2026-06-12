---
title: "natty sound settings lost every boot"
date: 2011-08-18
forum: Multimedia Software
---

### Post by mixmastamyk on 2011-08-18
Hi,

I'm regretting upgrading from Maverick to Natty.  Another of the problems I'm having is that I have to run alsamixer after every boot to fix my sound settings.  

I've even tried "sudo alsactl store" but no matter what my speakers are mute and microphone input wrong every time I boot.  :(

---

### Post by lidex on 2011-08-18
Try ```
sudo alsactl store 0
```

Next try these terminal commands:
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

### Post by mixmastamyk on 2011-08-22
Thanks, am trying this now.

I don't appear to have the second file you mention, /etc/init.d/alsa-restore .

---

