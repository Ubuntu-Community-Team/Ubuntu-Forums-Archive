---
title: "Microphone isn't working"
date: 2010-07-09
forum: Multimedia Software
---

### Post by Wawfulz on 2010-07-09
I've just installed Ubuntu 10.4. I've managed to get my speakers working, as I have everything else, apart from my microphone. I don't know why as I thought that if your speakers work, your microphone works, but I could be wrong.

I am a newbie to linux, so any help, could you please put it simply. Thanks ^_^

---

### Post by Sonsum on 2010-07-09
Welcome to Ubuntu!

Can I ask what model this computer is? Sometimes just knowing that helps a ton.

And is this an internal microphone (built into the laptop) or and external one (plugged into the laptop)?

---

### Post by lidex on 2010-07-10
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

---

### Post by Wawfulz on 2010-07-10
I'm afraid I don't know my PC's details. I bought it second hand and it looks custom built. I can only tell you the speed at shcih it's running. :/

@Lidex - I did the alt+F2 and typed in ```
 gnome-alsamixer
``` But it said that it couldn't find it.

This is not a built in microphone, and I'm using a desktop computer.

---

### Post by lidex on 2010-07-10
My previous post gives the command to install it.

---

