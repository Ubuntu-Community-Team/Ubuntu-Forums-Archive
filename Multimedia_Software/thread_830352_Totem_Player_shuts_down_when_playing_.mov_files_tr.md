---
title: "Totem Player shuts down when playing .mov files transferred from camera SD card."
date: 2008-06-15
forum: Multimedia Software
---

### Post by qphone on 2008-06-15
Firstly, I do in fact have the proper codecs (at least to my newbie knowledge) because I can go to apple.com/trailers and firefox plays all their trailers .mov files without a problem

So my question is...I've transferred a bunch of .jpeg's (plays fine) and .mov's (doesn't play) into /home/sony/Pictures/Panasonic Pictures and Videos/June 15, 2008 folder

**How come when I double click on a simple .mov file, Totem movie player opens up and then shuts off?**

Is there any way to watching a simple .mov files that's on my hard drive? I love ubuntu in the short time I've had this but something this simple is so aggravating!

---

### Post by Yuki_Nagato on 2008-06-15
I believe this is happening:

Firefox has a .mov plugin working.  But ONLY Firefox.  Your OS does not have it.  Here is how to fix it.  Go to System>Administration>Synaptic Package Manager and Search for "VLC".  Mark for installation, and allow all dependencies to be installed.

Now right-click on the .mov file, and "Open with other application"  Select VLC from the bottom.  Now it should play.

---

### Post by qphone on 2008-06-15
> **Yuki_Nagato said:**
> I believe this is happening:

Firefox has a .mov plugin working.  But ONLY Firefox.  Your OS does not have it.  Here is how to fix it.  Go to System>Administration>Synaptic Package Manager and Search for "VLC".  Mark for installation, and allow all dependencies to be installed.

Now right-click on the .mov file, and "Open with other application"  Select VLC from the bottom.  Now it should play.

[B]Thank You for the tip. VLC does in fact opens up BUT!...now I can only hear the audio (extremely choppy) but no video?????
[/B]
Am I missing another codec?

Thanks again for your help.

---

