---
title: "How do I set sound preferences?"
date: 2009-12-20
forum: Multimedia Software
---

### Post by Colin@oxford on 2009-12-20
I have just upgraded to karmic and find that the Preferences->Sound now opens the volume control rather than the "sound preferences" that Jaunty used to have.  The sound preferences used to let me select between OSS/ALSA/PulseAudio etc and also to select/test sounds for various events (login, email, alerts etc).  Where has this function been hidden now?

---

### Post by HappyFeet on 2009-12-20
Right click the little speaker icon in your panel.

---

### Post by Yellow Pasque on 2009-12-20
```
gstreamer-properties
```
Or install the old dialog if you wish: [http://launchpadlibrarian.net/33491183/soundproperties.tar.gz](http://launchpadlibrarian.net/33491183/soundproperties.tar.gz)
> I found a good GUI workaround for controlling gstreamer and event sound preferences. One can still run the old gnome-sound-properties with a couple of files. The attached file has 32bit/x86 and 64bit/x86-64 versions of the gnome-sound-properties program. Move the appropriate version of this file to /usr/local/bin and move the sound-properties.glade (this file is not architecture-dependent) to /usr/share/gnome-control-center/glade/ (you'll probably need to create this directory). [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/400973)

---

### Post by Colin@oxford on 2009-12-21
Thanks.

gstreamer-properties gives me the first set of properties (the OSS/ALSA choices) but not the second (fine-tuning of sounds for various events).

---

### Post by Ubuntaqua on 2009-12-22
> **Colin@oxford said:**
> Thanks.

gstreamer-properties gives me the first set of properties (the OSS/ALSA choices) but not the second (fine-tuning of sounds for various events).

Right-click

---

### Post by Colin@oxford on 2009-12-30
> 
**Ubuntaqua** says:  	

Right-click 

Sorry. Right-click what?  If I right-click the speaker icon as HappyFeet suggested I just see the same panel as the current "Sound" menu produces, which does not allow me to set (for example) the login sound.

---

### Post by andlinux on 2009-12-30
I've got the same problem, I want to disable the login sound (when you have to write your password) because it's annoying. In jaunty this was easy now I can't find how to disable it.

---

