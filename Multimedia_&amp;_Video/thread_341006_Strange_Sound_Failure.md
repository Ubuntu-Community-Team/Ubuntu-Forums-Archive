---
title: "Strange Sound Failure"
date: 2007-01-18
forum: Multimedia &amp; Video
---

### Post by Fear_of_C on 2007-01-18
When Ubuntu boots, the sound works normally and seems to work normally so long as I only play sounds through a single application, and that application does not affect the sound settings.  The sound completely stops playing at some point , generally when changing the volume or attempting to test through the preferences panel.  It only re-enables on a full reboot; I have tried restarting ALSA, switching to OSS, and restarting Gnome.  I have also tried alsamixer, which failed to achieve anything.

System Info:
Edgy Eft (6.10) x86_64
Laptop Model: [Asus A8JS]("http://www.rothlaender.net/index2.htm")

aplay -l output:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v excerpt:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1447
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

I read that the system may be confusing the webcam for a soundcard, so I installed the webcam drivers and used it, which had no effect.

I found one instance of a [similar problem.]("http://www.ubuntux.org/kubuntu-6-06-no-sound-with-via-8237-ac97-chip")

---

### Post by Fear_of_C on 2007-01-18
Come morning, the volume controls and sound have started to work - seemingly gradually and in arbitrary chunks.  The keyboard shortcut, however, has no effect.

This might be related to adding ""options snd-hda-intel position_fix=1 model=3stack" to /etc/modprobe.d/alsa-base

---

### Post by Fear_of_C on 2007-01-19
The sound is once again failing long after the computer has been running, and it no longer seems to obey any kind of logic is to when or why it fails.  It is worth noting that ALSA detects 2 sound cards, an analog and a digital version of the Intel HDA.  Neither one, however, responds to sound tests when the system is silent.

It is also worth noting that one of the two (the analog one right now) displays the following text rather than silently failing the sound test:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available.

Is there any way to determine if another process is somehow hogging this sound card?
After looking more extensively, I used lsof to determine that firefox was hogging the sound card; killing and restarting firefox seems to have fixed the problem, at least for the moment.

---

### Post by Zogg on 2007-02-07
I have exactly the same problem, the difference is that im on HP dv2000 laptop.

---

### Post by veratyr on 2007-02-09
options snd-hda-intel position_fix=1 model=3stack fixed my sound issues with the a8js. I have the webcam working as well. I'm using 32bit Edgy though.:confused:

Just out of curiousity have you disabled the start up "chime" in the bios? If so try enabling it. I disabled it once and my sound stopped working. Not sure if it was related or not but it's worth a try.

---

### Post by desiobu on 2007-09-04
Any resolution?  I'm having the same problem at the moment (different sound device, same errors).

---

