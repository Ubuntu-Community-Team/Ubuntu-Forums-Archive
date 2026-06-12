---
title: "Strange audio corruption/mutilation (Ubuntu 10.04, Toshiba NB300)"
date: 2010-05-09
forum: Multimedia Software
---

### Post by thePowersGang on 2010-05-09
I have a Toshiba NB300 netbook running Ubuntu 10.04 and it appears to have a strange bug somewhere in the audio handler.

When attempting to play audio from an application more than once per instance (I think, either that or within a largeish time period) the audio will be turned into a series of clicks that approximates the actual sound (on most music tracks, the beat is discernible).
   The effect is similar to the over-amplified audio clipping effect, just excessively applied.

Does anyone know what could be causing this and if there is a fix to it?

(As a side note, this effect really kills my ears :))

---

### Post by hatemben on 2010-06-03
Just noticed this week, as I didn't use much audio/video before. I have to investigate more on it, using NB 300 also with netbook remix 10.04.

-Hatem

---

### Post by Gargintua on 2010-07-08
same happens to me, any solution?

---

### Post by thePowersGang on 2010-07-08
According to another post I saw while I was researching another bug, it's a problem between the audio chipset and pulseaudio.
A solution is to remove pulseaudio, this will disable the volume hotkeys, but will also stop this artifact from occurring. (You still can use an ALSA control app to change the volume, such as alsamixer)

This seems to be a bit of a hack, especially since if you use aptitude to install something, it automatically reinstalls pulseaudio for you. Is anyone able to find out where this bug actually is?

---

### Post by lidex on 2010-07-08
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by thePowersGang on 2010-07-08
```

~$ uname -a
Linux sonata 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

```

```

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

~$ dpkg -l | grep "alsa"
ii  alsa-base              1.0.22.1+dfsg-0ubuntu3     ALSA driver configuration files
ii  alsa-utils             1.0.22-0ubuntu5            ALSA utilities
ii  bluez-alsa             4.60-0ubuntu8              Bluetooth audio support
ii  gnome-alsamixer        0.9.7~cvs.20060916.ds.1-2  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa     0.10.28-1                  GStreamer plugin for ALSA
ii  libsdl1.2debian-alsa   1.2.14-4ubuntu1.1          Simple DirectMedia Layer (with X11 and ALSA

```

```

~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC272

```

The laptop is a Toshiba NB300 Netbook (Part #PLL3EA-006007)

---

### Post by lidex on 2010-07-08
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by thePowersGang on 2010-07-08
That seemed to make it a little less common, but the bug still occurs (with pulseaudio installed)

I was able to have three mplayer instances open with no problem, but when two of them were closed, the sound failed again.

---

### Post by lidex on 2010-07-09
Look at appendix b here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
and this:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html]("http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html")

---

