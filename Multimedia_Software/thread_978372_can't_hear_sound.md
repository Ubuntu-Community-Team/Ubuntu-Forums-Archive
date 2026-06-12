---
title: "can't hear sound"
date: 2008-11-11
forum: Multimedia Software
---

### Post by geekyBar on 2008-11-11
I'm new to Ubuntu and I can't hear any sound. Not no youtube, .mp3 or .wmv files. Not even when I play 4-in-a-row.
Only time I do hear sound is when I'm asked to enter user name on boot. I can hear drums.
I followed Comprehensive Sound Problem Solutions Guide

when I type into the terminal:
aplay -l

I get:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

according to the guide my sound is muted so I type to the terminal : alsamixer.
But then I see only one slide-bar, and it's on max volume.

Please help me hear sound.

---

### Post by psyke83 on 2008-11-11
The "Comprehensive" guide is a bit outdated now that PulseAudio is used by default. You need to unmute your Master/PCM levels for your physical sound card.

Running "alsamixer" with no parameters will open the PulseAudio mixer (as of Intrepid, the default ALSA device is now "pulse"), which isn't what you want to do.

In order to access your physical card's controls, run:
```
$ alsamixer -Dhw
```

---

### Post by geekyBar on 2008-11-11
I did as you said and I got a similar screen with a about ten slide-bars. but all of them were on max volume.:( 
how is it possible for me to hear the drums when I boot, but hear nothing at all after?:confused:

---

### Post by psyke83 on 2008-11-11
PulseAudio may have selected the incorrect sound card. Do this:

1. Install the package "padevchooser", then launch the PulseAudio Device Chooser applet (Applications/Sound). Open PulseAudio Volume Control (accessible by left-clicking the applet icon).

2. Play some content with audio in Totem, and leave it running.

3. While audio is playing, go to the PulseAudio Volume Control applet, Playback tab. Right-click on the entry for Totem and choose "Move stream...".  There should be at least two options - try them all.

---

### Post by geekyBar on 2008-11-11
I don't really know much about hardware. my dad says I have only one sound card on my computer.:confused:

---

