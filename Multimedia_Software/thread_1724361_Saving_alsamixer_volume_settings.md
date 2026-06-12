---
title: "Saving alsamixer volume settings"
date: 2011-04-08
forum: Multimedia Software
---

### Post by Codemagnet on 2011-04-08
Hi all.

When i installed Ubuntu, everything worked fine, sound drivers installed automatically and volume was perfect.

Then one day as I was talking to a friend on skype, I tried changing the output to speakers from my headset during the call and i didnt get any output. I tried changing a few settings, can't remember which ones exactly until I noticed someone had pulled the audio cable from the back of my PC.  I replaced it but I started getting very very low sound.

I found out about alsamixer and when I ran it, I found that the volume on that device was turned down, i turned it up and voila! sound back to normal.

However, now when I reboot, my sound goes down again.  I have tried deleting the asound.state file and running the save command, "sudo alsactl store 0" I think, as someone suggested, but no cigar.  There must be a way to save these settings surely.

Any help would be much appreciated.  Thanks

---

### Post by lidex on 2011-04-10
First try these terminal commands:
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

### Post by Codemagnet on 2011-04-13
Sorry for the sluggish reply. That first suggestion did it.  Thanks mate, much appreciated.

---

### Post by noletolucas on 2011-07-03
Yeah. Commenting out the "load-module module-device-restore" worked for me too.

---

