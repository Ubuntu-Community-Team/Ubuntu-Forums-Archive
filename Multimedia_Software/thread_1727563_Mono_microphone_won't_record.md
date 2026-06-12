---
title: "Mono microphone won't record"
date: 2011-04-12
forum: Multimedia Software
---

### Post by zonedabone on 2011-04-12
I've had this problem on ubuntu before, and I remember that I had to install a program from synaptics package manager and change the noise removal settings. This worked on someone else's mono mic, and I'm wondering if anyone knows which program changes the system setting for noise cancellation.

---

### Post by lidex on 2011-04-12
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

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. 

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

### Post by squee on 2011-04-15
I have tried this but doesnt work for me. Running 11.04b and laptop specs are below.

The mic works perfectly on windows so it is working.

It is a mono mic but there is no option in the sound preferences to make it mono. In the Pulse options I have the right set to 0. I've tried it with left too. Anything else I can try?

---

