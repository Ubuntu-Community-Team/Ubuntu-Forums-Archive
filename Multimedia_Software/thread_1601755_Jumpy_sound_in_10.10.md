---
title: "Jumpy sound in 10.10"
date: 2010-10-20
forum: Multimedia Software
---

### Post by Huggzorx on 2010-10-20
Hey,

After upgrading to 10.10, I have been having all sorts of audio problems, mostly with sound skipping like a record. It happens with sounds both streamed from the internet and from my own system. It also seems to affect flash videos, but that might just be the video moving to sync with the sound? The weirdest thing is that if I move the mouse (either the laptop trackpad or the external mouse), it stops doing it, but as soon as I stop moving the mouse, it skips again.

Could this be a problem with pulseaudio?

---

### Post by tommcd on 2010-10-20
> **Huggzorx said:**
> 
Could this be a problem with pulseaudio?
I suppose it could be. This sounds like an unusual problem. How high is your CPU usage when the dound skips? Pulseuaudio is known to be a huge resource hog.
It is easy enough to rule out pulseaudio as the problem by simply removing it:
```
sudo apt-get remove --purge pulseaudio gstreamer0.10-pulseaudio
```
Then run ```
gstreamer-properties
``` and set everything to alsa. Then reboot just to to make sure that pulseadio is killed.
If you ever want to reinstall pulseaudio, just reinstall *pulseaudio* and *gstreamer0.10-pulseaudio*.

As an alternative to removing pulseaudio, here is an article that shows you how to turn pulseaudio on and off at will instead of removing it:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/)
Hope this helps.

And welcome to the Ubuntu forums!

---

### Post by jmatties on 2010-10-20
small typo:
```
sudo apt-get remove --purge pulseaudio gstreamer0.10-pulseaudio 
```

---

### Post by Huggzorx on 2010-10-31
Hi guys, sorry for the late reply. I tried uninstalling pulseaudio and replacing with alsa, but that doesn't seem to have fixed the problem (plus I can't change the volume with alsa).

I'm thinking it must be some strange hardware driver compatibility issue with 10.10. I'll probably just go back to 10.04 for now, unless anyone else has any ideas.

Running a Samsung R591 with 32 bit ubuntu.

Thanks

---

### Post by tommcd on 2010-11-01
> **Huggzorx said:**
> ... plus I can't change the volume with alsa).
You can easily change the volume levels with **alsamixer** from the terminal. If using the terminal is not to your liking, then you can install **alsamixer-gui** or **gnome-alsamixer** and have a GUI app for controlling sound.
> **Huggzorx said:**
> 
I'll probably just go back to 10.04 for now, unless anyone else has any ideas.

You could try doing a clean install of Ubuntu 10.10. This is often the fastest way to fix a dist-upgrade that did not go well. I always do clean installs of Ubuntu. It takes all of 15 minutes, then perhaps another 60 minutes (at the most) to get all the updates and install all the programs I use.

---

