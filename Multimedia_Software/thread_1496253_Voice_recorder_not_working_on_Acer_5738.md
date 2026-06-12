---
title: "Voice recorder not working on Acer 5738"
date: 2010-05-29
forum: Multimedia Software
---

### Post by Anand Jayaraman on 2010-05-29
Hi,

I have Ubuntu Lucid Lynx installed on my Acer 5738 laptop.

I am unable record sound using the Sound Recorder. I am unable to do any voice chat.

My microphone is not muted.

It has never been working in any previous ubuntu releases for me.

I have done sufficient research on the forums and tried out some of the suggestions mentioned but it has not worked for me.

Could you please help?

Regards,
Anand

---

### Post by lidex on 2010-05-30
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

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

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

### Post by Ceezey77 on 2010-07-12
Hi Anand,

I have the same laptop - I recently reinstalled Lucid on my machine due to some earlier problems with Virtualbox (unrelated) and ran a synaptic update on the fresh install. Following that I installed guvcview which is a neat little webcam video recording app and had no problems with sound.


Often I find I need to go into [System]->[Preferences]->Sound and within the [Input] tab make sure the Input volume is AT LEAST 100% and that I have 'Microphone 2' selected - The microphone on these Acers isn't particular sensitive by my reckoning.

I've attached a screen shot of the window as mentioned above. 

I hope this helps.

---

