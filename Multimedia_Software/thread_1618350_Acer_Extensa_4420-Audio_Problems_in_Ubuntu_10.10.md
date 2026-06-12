---
title: "Acer Extensa 4420-Audio Problems in Ubuntu 10.10"
date: 2010-11-10
forum: Multimedia Software
---

### Post by KWS48 on 2010-11-10
Ok, I just installed Ubuntu 10.10 and was very happy, that my wireless card was finally recognized, and I could connect my Acer Extensa 4420 after giving up on all fixes offered here in the Forums and elewhere.
Everything seemed to be working fine.

Then I decided to play some music files.  While using my headphones I have sound, but if I unplug them, nothing comes from the speakers.

I clicked on my sound icon, and checked "sound preferences".  There it showed that there was sound coming from my speakers ( the sound bars ) yet nothing was coming out.

Likewise I use an online language program.  I need to use my microphone for it. It recognizes the microphone as "Linux Microphone" but could not configure it.  Then I went to "sound recorder" to check if my microphone was working.  I cannot record anything.  It immediately asks me if I want to "save file", even though I have recorded nothng.  There is no way to record sound.  So I presume my microphone is not working.  In sound preferences no input devices show.  There is simply a pink blank box and the slide bar etc are greyed out.

Anyone have any idea how I can fix this problem?  I have gone through the threads and found only one other post that matched, and there have been no replies.:(

---

### Post by lidex on 2010-11-11
> **KWS48 said:**
> Ok, I just installed Ubuntu 10.10 and was very happy, that my wireless card was finally recognized, and I could connect my Acer Extensa 4420 after giving up on all fixes offered here in the Forums and elewhere.
Everything seemed to be working fine.

Then I decided to play some music files.  While using my headphones I have sound, but if I unplug them, nothing comes from the speakers.

I clicked on my sound icon, and checked "sound preferences".  There it showed that there was sound coming from my speakers ( the sound bars ) yet nothing was coming out.

Likewise I use an online language program.  I need to use my microphone for it. It recognizes the microphone as "Linux Microphone" but could not configure it.  Then I went to "sound recorder" to check if my microphone was working.  I cannot record anything.  It immediately asks me if I want to "save file", even though I have recorded nothng.  There is no way to record sound.  So I presume my microphone is not working.  In sound preferences no input devices show.  There is simply a pink blank box and the slide bar etc are greyed out.

Anyone have any idea how I can fix this problem?  I have gone through the threads and found only one other post that matched, and there have been no replies.:(
Need more info please. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by shadrack111 on 2010-11-13
[http://www.alsa-project.org/db/?f=a5ed0066e4ccb1b42565ff5c6688a6fc4c2d4092](http://www.alsa-project.org/db/?f=a5ed0066e4ccb1b42565ff5c6688a6fc4c2d4092)

---

### Post by shadrack111 on 2010-11-13
sry im new to this. i have the same problem. my mic worked with 10.10 but now i cant get it to work. im getting so aggravated. ubuntu is great if your good with computers. i want to stick with ubuntu. but something is always going wrong.

---

### Post by lidex on 2010-11-13
> **shadrack111 said:**
> sry im new to this. i have the same problem. my mic worked with 10.10 but now i cant get it to work. im getting so aggravated. ubuntu is great if your good with computers. i want to stick with ubuntu. but something is always going wrong.

Your mics are turned off in the mixer section.
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

### Post by Vanish00 on 2010-11-20
Thank you, this fixed my microphone issue!  Although, I had to use:

```

sudo apt-get install pavucontrol

```

---

