---
title: "[SOLVED] Miro: Video but No Sound"
date: 2008-05-26
forum: Multimedia Software
---

### Post by wyth on 2008-05-26
I've been searching for this for a few days, with no luck either here, the (nearly useless) Miro forums, or Google.

The issue: After a clean install, I can no longer get sound out of any video Miro plays.  Everything else works fine.

I previously had sound on Miro in Gutsy.  I did an upgrade to Hardy, and still had sound.  For a number of reasons, I went back and did a clean install, which led to no sound.

I'm not using Pulse (it didn't work with Pulse either), I'm back on the latest ALSA drivers, because they get me glorious surround sound on my Lenovo.

Any ideas on this?  I used to use Miro quite a bit, but without sound, it's rather useless.

---

### Post by zeny on 2008-05-26
What is your sound card?

What happens when you go to system>Preferences>sound and then run the test? 

lspci -v | grep -i audio <-- run that command

aplay -l <--- that too

:)

---

### Post by wyth on 2008-05-26
Heya -- here we go:

[LIST]
[*]System-Prefs-Sound tests all work (it's set to ALSA)
[*]Sound Card: Intel 82801H HD audio controller -- it's in the ICH8 family
[*]lspci gives the same: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
[*]aplay -l gives:
[/LIST]
 ```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Everything else works just fine, except the sound on Miro.  hmm...

---

### Post by wyth on 2008-05-27
bump

---

### Post by wyth on 2008-05-28
just gonna give this a little nudge up top

---

### Post by wyth on 2008-05-28
*yawn*
*stretch*
*bump*

---

### Post by garoth2 on 2008-06-08
I'm having the same issue

Intel HDA driver (ALC888) on an Asus m50sv laptop

---

### Post by wyth on 2008-06-09
I'm almost positive this is a xine problem.  I tried playing one of my downloaded videos via Gxine, with the same problem.  Same video works in Totem and VLC.

*EDIT*

Except for the fact that I just changed it to use Gstreamer, and the same issue persists.  Annoying...

---

### Post by garoth2 on 2008-06-10
Strangely, I tried playing the same videos in Miro again the following day and it seems to work perfectly with both gstreamer and xine. I'm not even sure if I had rebooted or not.

I should note that I *was* able to play the videos miro downloaded in both totem-gstreamer and xine-ui while miro was having the problem, so my issue may have been different.

---

### Post by markbuntu on 2008-06-11
Do you have gstreamer0.10-alsa?

It is the gstreamer plugin for alsa.

You should also have libasound2-plugins which are alsa plugins for jack and OSS and pulseaudio.

 and alsa-oss which is the alsa wrapper for OSS apps.

and xmms2-plugin-alsa which is the xmms2 plugin

and the alsaplayer-alsa which is the PCM player for alsa

and libesd-alsa0 which allows multiple audio streams on one device in alsa.

Some of these you should already have, the rest you should get. Then you can change you Sound settings to alsa from automatic and everything should work.

---

### Post by wyth on 2008-06-11
**Checklist:**

[LIST]
[*] gstreamer010-alsa: check
[*] libasound2-plugins: not installed, trying it
[*] alsa-oss: check
[*] xmms2-plugin-alsa: not installed, trying it
[*] alsaplayer-alsa: not installed, trying it
[*] libesd-alsa0: check
[/LIST]
      
[B]Results:
[/B]
[LIST]
[*]After installation of non-installed items, Miro still had no sound
[*]Reboot: Still no sound, with either gstreamer or xine set as the default for playback.
[/LIST]
*grumble grumble grumble*

I miss Miro, I used to use that application.

---

### Post by markbuntu on 2008-06-12
Is your System/Preferences/Sound set to alsa?

Pulseaudio caused all sorts of problems like this for me until I disabled it.

---

### Post by wyth on 2008-06-12
Oh yeah most definitely set to Alsa.

---

### Post by wyth on 2008-06-29
There have been some kernel and xorg updates in the past two weeks, and I can report that 

**MIRO SOUND IS NOW WORKING.** \\:D/

I hope it's working for you, too.

---

### Post by markbuntu on 2008-06-29
You should mark this thread as solved in thread tools.

---

### Post by wyth on 2008-06-29
> **markbuntu said:**
> You should mark this thread as solved in thread tools.

Whoops -- thanks.  Done and done.

---

