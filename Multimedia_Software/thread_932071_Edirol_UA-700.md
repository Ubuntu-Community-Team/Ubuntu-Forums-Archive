---
title: "Edirol UA-700"
date: 2008-09-28
forum: Multimedia Software
---

### Post by ztomic on 2008-09-28
I've been fighting with my Edirol sound board for several months and now I think I have a little solution that may help new users set it up. If anyone wants to write a how-to, you're welcome to do so but this is an informal post.

step 1: ```
sudo nano /etc/modprobe.d/alsa-base
```
comment out the section for snd-usb-audio. it should look like this:
```
#options snd-usb-audio index=-2
```

step 2: Select **System -> Preferences -> Sound** and make sure that the PortAudio sound server is selected for all fields.

That's it! Now start jack and Renoise or EnergyXT2.

*this should be moved to hardware probably*

---

