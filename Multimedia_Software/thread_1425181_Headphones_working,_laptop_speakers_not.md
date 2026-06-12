---
title: "Headphones working, laptop speakers not"
date: 2010-03-08
forum: Multimedia Software
---

### Post by tonemgub on 2010-03-08
Hi,
I just bought a new hp probook laptop and I wanted to try ubuntu karmic 9.10. The installation is fine except for the sound, which I can only hear through my headphones, but not through the laptop's speakers. I've tried everything google told me to, including trying up pretty much all of the possible combinations in alsamixer, but still no success. 
The output of ```
aplay -l
``` seems strange (two cards 0):
```
**** List of PLAYBACK Hardware Devices *****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
    Subdevices: 1/1
    Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
    Subdevices: 1/1
    Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
    Subdevices: 1/1
    Subdevice #0: subdevice #0
```
Any ideas? Any more information required?
Thank you!

---

### Post by Jackelope King on 2010-03-08
This worked for me on my **dv3510nr**, but the problem you describe is exactly the problem I had. Depending on your model, it might not do the trick, so back up a copy of your alsa-base.conf file first.

From [this thread]("http://ubuntuforums.org/showthread.php?t=1258788"):

> **dannymac64 said:**
> After spending many, many hours searching for solutions concerning my dv3-2155mx (Jaunty 9.04 64 bit), I thought I'd post my successes in hopes that it would help someone:

Flawless sound and internal mic functionality:
1. Install the latest ALSA drivers.  I installed 1.0.20 via this link, but watch out for his tar extract commands, which didn't work for me:
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

2. Edit alsa-base.conf:
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
3. Then add (note the model is **hp-dv5**):
```
options snd-hda-intel model=hp-dv5 enable_msi=1
```


---

### Post by tonemgub on 2010-03-10
Thank you! 
The line you provided me was not working as is, but I found out that using ```
model=laptop
``` does the trick!

---

### Post by daveola on 2010-06-07
Just as a note for anyone doing a search, I had this same problem but ended up having a different solution.

It turned out that switching between mute/unmute while switching between speakers/headphones ended up putting my speakers in a state where they wouldn't unmute, even after reboot.  This is with the (patched) pcc_acpi module (though trying to unload it didn't help either).  Furthermore none of the alsamixer settings showed anything off or muted, and trying other drivers (like OSS) didn't help either.  My guess is that something was turned off in the actual sound card, something that was saved/restored each boot.

Finally I solved the problem by playing with switching between mute and unmute while plugging the headphones in and out, and voila, my speakers started to work again!

Might be worth others trying if they encounter this problem.

---

