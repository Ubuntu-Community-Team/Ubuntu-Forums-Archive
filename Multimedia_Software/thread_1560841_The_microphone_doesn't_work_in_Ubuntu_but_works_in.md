---
title: "The microphone doesn't work in Ubuntu but works in Windows and Fedora !"
date: 2010-08-25
forum: Multimedia Software
---

### Post by axrl on 2010-08-25
Hi,

Leaving the microphone connected (it works good in Fedora and in Windows), when I switch to Ubuntu 10.04 it's totally ignored  !

I don't know how to fix this issue !  

I tried "System" -> "Preferences" -> "Sound" but it seems there one has to choose either an OUTPUT configuration, either an INPUT configuration but NOT both of ones !  Anyway trying the input configuration and recording a voice (then of course listening to it with an output configuration) the microphone didn't record anything !

Same issue with "Empathy IM Client" or with other software.

How is this possible ?  I think Fedora manage the same way the microphone, isn't it ?

Thanks.

Axrl

---

### Post by dv3500ea on 2010-08-25
Have you tried increasing the input volume. Also, make sure you choose the correct connector.

---

### Post by axrl on 2010-08-25
I don't understand the way how to use this software !  Indeed if I select a "device for sound input" then I have NO sound OUTPUT !  And vice-versa.

Axrl

---

### Post by axrl on 2010-08-25
OK I found that certain hardwares in the "sound" software are "input and output".

I have the classic motherboard with 

1) a stereo line out ;
2) a stereo line int ;
3) a mono microphone line in with bias current.

Which hardware must I choose in the list ?

Note : I tried all the input hardwares and none of this activates my microphone !  (Its works properly in Fedora and Windows !)

Thanks.

---

### Post by lidex on 2010-08-25
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

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

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

### Post by axrl on 2010-08-26
I didn't find the menus you are describing.  Here you are 3 different screen-shots of my AlsaMIxer.  

I don't understand how to use this software if this is compulsory.

I read other posts about 'microphone doesn't work in Ubuntu10.04' but nothing helped me.

Axrl

---

### Post by lidex on 2010-08-27
> **axrl said:**
> I didn't find the menus you are describing.  


It's gnome-alsamixer, not alsamixer.

Do this please.Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by axrl on 2010-08-27
'ubuntu-bug audio' : done, it makes a report and I sent it.

By the way I installed Gnome-alsamixer.  I'll try to understand how it works...

Thanks.

---

