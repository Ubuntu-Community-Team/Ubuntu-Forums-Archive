---
title: "Dell Laptop D610 Microphone not working"
date: 2011-03-01
forum: Multimedia Software
---

### Post by stephenstop on 2011-03-01
Hello all,

I have a Dell Latitude D610 that was given to me and I currently have Ubuntu 10.04 installed.  I am trying to get the internal microphone working for gchat.

If I go to System-->Preferences-->Sound-->Hardware it says:
Choose a device to configure and Internal Audio, 1 Output/1 Input Analog Stereo Duplex is highlighted.

Settings for the selected device:
Analog Stereo Duplex is selected on the dropdown menu.

When I select the Input tab:
Input Volume is at 100% 
the box for Mute is unchecked
Connector Analog Microphone/Microphone 1 is selected on the drop down menu for Connector and 
the device for sound input: Internal Audio Analog Stereo is selected.

How can I configure my microphone to work?

---

### Post by lidex on 2011-03-01
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

