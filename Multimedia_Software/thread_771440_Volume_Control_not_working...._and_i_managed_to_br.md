---
title: "Volume Control not working.... and i managed to break all of the video codecs"
date: 2008-04-27
forum: Multimedia Software
---

### Post by Ponomous on 2008-04-27
**EDIT::  Thanks to mgmiller for the help and I managed to fix all of the codecs.**


Hey, so I have looked around and cant find a fix that works for this.  I have a g15 keyboard and have almost everything working on it except for the volume control wheel.  When i turn it the volume icon pops up and the bar slides up as if it is changing the volume but no actual change occurs.  Any ideas on whats broken?

I am running 7.10

also on a side note, i broke all of the video codecs when I was trying to get .mkv's to work. now i cant play any video, the audio works still but the standard green messed up screen shows up when it tries to decode the video. 

Thanks

---

### Post by mgmiller on 2008-04-27
> When i turn it the volume icon pops up and the bar slides up as if it is changing the volume but no actual change occurs. Any ideas on whats broken?

Go to System > Preferences > Sound
On the Devices Tab, below the "Default Mixer Tracks"
drop down is a list of different tracks.  
I suggest you select the "Master", which should be the first one.
This sets what your keyboard volume control is doing.

---

### Post by Ponomous on 2008-04-28
Yeah I tried that to no avail.   I have no idea what I did...  Any other ideas?

---

### Post by mgmiller on 2008-04-28
Try right clicking the speaker icon in the top panel and select Preferences.  Make sure the right item is selected.  Sometimes, this area will show a different setting from the other area I told you to set.  You can also experiment with the drop down list at the top of this box.  I have mine set to VIA 8237 (Alsa mixer) and the first entry below, Master, is the one high lighted.

---

### Post by Ponomous on 2008-04-28
HAHA, your not gonna believe this.  I had everything right but i had the scroll wheel associated with the wrong control, so every time i did it it did adjust the volume but even if i changed the association in the volume control it would still do the old one.

GO ME!:lolflag:

thanks for your help :)

---

### Post by mgmiller on 2008-04-28
LOL, glad I could help. :guitar:

:popcorn:

---

