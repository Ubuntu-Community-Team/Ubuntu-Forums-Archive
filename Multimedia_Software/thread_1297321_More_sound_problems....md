---
title: "More sound problems..."
date: 2009-10-21
forum: Multimedia Software
---

### Post by chrisklepka on 2009-10-21
Ok so I just decided to get Ubuntu on this computer. I hate Windows Vista so I got rid of all of it. So now I sit here with Ubuntu, which so far I love... except for one thing: NO SOUND! I have been searching around for a couple of fixes and in my process, I have come across this forum and it's sticky. I tried everything up there but some things would give me errors and others did nothing. One thing in particular that was said to be done was to turn off External Amplifer's swtich. Well... there is none. I don't see it in alsamixer or the Audio Mixer preferences.

Now I am a TOTAL NOOB at Ubuntu and Linux so I need full details on what to do... I understand Terminal is where most of this stuff is going to be changed, so shoot away suggestions. Here are some specs.

chris@chris-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[http://support.gateway.com/s/Mobile/2008/GodzillaFX/1015340R/1015340Rsp2.shtml](http://support.gateway.com/s/Mobile/2008/GodzillaFX/1015340R/1015340Rsp2.shtml) - My laptop

---

### Post by Mark_in_Hollywood on 2009-10-21
> **chrisklepka said:**
> Ok so I just decided to get Ubuntu on this computer. I hate Windows Vista so I got rid of all of it. So now I sit here with Ubuntu, which so far I love... except for one thing: NO SOUND! I have been searching around for a couple of fixes and in my process, I have come across this forum and it's sticky. I tried everything up there but some things would give me errors and others did nothing. One thing in particular that was said to be done was to turn off External Amplifer's swtich. Well... there is none. I don't see it in alsamixer or the Audio Mixer preferences.

Now I am a TOTAL NOOB at Ubuntu and Linux so I need full details on what to do... I understand Terminal is where most of this stuff is going to be changed, so shoot away suggestions. Here are some specs.

chris@chris-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[http://support.gateway.com/s/Mobile/2008/GodzillaFX/1015340R/1015340Rsp2.shtml](http://support.gateway.com/s/Mobile/2008/GodzillaFX/1015340R/1015340Rsp2.shtml) - My laptop

Please tell me if you see an icon on your panel that resembles a plug and some cable. It's grey on my 'puter.

If you see this, you have Pulseaudio. Left click this. From the drop down menu, open Volume Control. Find the small speaker icon. Click it. Play something with sound. Play with the volume sliders. You can gang them with the "shield" icon.

Let me know, and if this solves the problem, please mark the post solved under Thread Tools.

---

### Post by chrisklepka on 2009-10-21
If by panel, you mean the top bar, then no I do not. I think during one of the fixes it was removed. If I need to reinstall it, how would I do so?

---

### Post by chrisklepka on 2009-10-21
Ok get this... I installed Pulse Audio following this:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

And I am looking at some part of Pulse Audio that shows the signals of my sound card... bars here are moving back and forth with the music playing on Youtube, but nothing is coming out of the speakers....

---

### Post by chrisklepka on 2009-10-21
Another thing I noticed: It says Analog and there is no option for Digital... maybe this is it. Does anyone know how to bring about the option to use the Digital output opposed to the Analog one?

YEP. Just found headphones and plugged them in. NOTE TO ALL PEOPLE: LOWER VOLUME BEFORE DOING THIS.

nothing will come out of the speakers, only headphones.

---

### Post by chrisklepka on 2009-10-21
Solved:

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

Finally. I can't seem to mark this as solved though.

---

