---
title: "PulseAudio not working?"
date: 2008-08-14
forum: Multimedia Software
---

### Post by davethewave83 on 2008-08-14
Hello! 
I have VirtualBox running, when I try to listen to music or play any sound anywhere else on Ubuntu outside of VB it says it cannot play because the device is in use. I read about it and enabled ESD with full ALSA. It didn't help so I read I needed PulseAudio but when I checked in the package manager it says I already have PulseAudio installed. So my question is: Why isn't it mixing properly?:confused: Thanks!

---

### Post by markbuntu on 2008-08-14
Try my guide, it does not say anything about running in VB but it will help you get a handle on how sound works in Ubuntu. You should probably just read it before trying anything.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by davethewave83 on 2008-08-15
Ok I will give it a shot, but for someone who is fairly new to linux and is used to being spoon fed by windows, this looks like a lot of hassle :lolflag:

Thanks for the reply!

---

### Post by davethewave83 on 2008-08-15
A lot of things give me multiple playback now, but Audacity does not see any sound output cards now.

---

### Post by davethewave83 on 2008-08-15
I am having conflicts with Audacity and gxmms2, only one can work at a time. Also how do I find out what device I am using? I'm running Basilisk II and there is no sound, I don't know which sound device I am using, I have everything in the sound control to go through PulseAudio but I am not sure where to point BasiliskII for this. It is currently set at output /dev/dsp and mixer /dev/mixer Any assistance would be greatly appreciated Thank You!

---

### Post by markbuntu on 2008-08-15
Yes, that is to be expected, you can use the pasuspender command when you launch audacity and it will work but not with everything else. To do that go to System/Preferences/Main Menu. Double click on audacity and you will get the Launcher Properties window. In the Command: window put
```

pasuspender audacity

```

This will suspend pulseaudio while you run audacity and restore it when audacity closes. It is the best than can be done so far. 

The big problem is that audacity was written to work with portaudio, which is not used in these distributions so there are a bunch of half-assed workarounds to get it to work with OSS and ALSA and Jack. These are only semi-functional and there seems to be no progress by the audacity devs to improve them. For example, if the OSS plugin actually worked properly, audacity would have no problem with OSS or ALSA (through aoss) or pulseaudio, Same thing with the alsa plugin. 

I recently tried it with jack again and when you choose the jack plugin it crashes and then appears in the jack connections box, lol.

I gave up on audacity a long time ago and moved to ardour. It works fantastically, a truly professional recording/mixing suite written and maintained by the same guys who made jack.

---

