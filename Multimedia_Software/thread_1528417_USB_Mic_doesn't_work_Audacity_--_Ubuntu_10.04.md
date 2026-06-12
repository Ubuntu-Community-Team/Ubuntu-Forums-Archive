---
title: "USB Mic doesn't work Audacity -- Ubuntu 10.04"
date: 2010-07-10
forum: Multimedia Software
---

### Post by iamthemooseking on 2010-07-10
Hello World!

I'm running Ubuntu 10.04, using Audacity 1.3.12 beta... and trying to get it to work with a USB Mic.  Ahh!
In Audacity ALSA I/O preferences, I can select the USB mic.  But when I record, the input meter stays at about half-way and does not fluctuate when I speak into the microphone... I can hear myself very faintly on the playback... but it is very quiet and there is a loud buzzing.  There are no mechanical reasons for this buzzing, such as computer fan, etc...

Also, I cannot find the USB mic in Ubuntu Sound Prefereces...

This is from "Device Info" in audacity:

Selected capture device: 5 - ALSA: USB Device 0x1940:0xac02: USB Audio (hw:1,0)
Selected playback device: 11 - ALSA: default
Supported Rates:
    44100
    48000
Unable to open Portmixer

---

### Post by lidex on 2010-07-10
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then use pulseaudio volume control (pavucontrol) or 'Sound Preferences' to select and unmute your mic in 'Input Devices' tab.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

Then have a look here:
[http://forum.audacityteam.org/viewtopic.php?p=75044#p75044]("http://forum.audacityteam.org/viewtopic.php?p=75044#p75044")

---

### Post by ajgreeny on 2010-07-10
I prefer the cli version of ```
alsamixer
``` which may offer you a choice of more than one microphone.  Try that and see if it will do what you need.

---

