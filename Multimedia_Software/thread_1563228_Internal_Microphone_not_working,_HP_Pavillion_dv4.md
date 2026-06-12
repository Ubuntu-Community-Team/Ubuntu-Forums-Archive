---
title: "Internal Microphone not working, HP Pavillion dv4"
date: 2010-08-28
forum: Multimedia Software
---

### Post by vidvisionify on 2010-08-28
Heyhihello. I have a HP Pavillion dv4 1313dx that has been running Ubuntu Lucid Lynx 10.04 wonderfully, but I am getting nothing out of the microphone.

I am a VERY beginning user (All I really know how to do in terminal is copy/paste, cd, ls, and, chown) and if I can fix this easily, I'd love it.

I already know to check the sound preferences, and nothing is picked up on the microphone, but I think it's there.

If you help me, I'll give you a cookie*.

[SIZE="1"]*Cookie meaning, I'll be really, really grateful.[/SIZE]

---

### Post by vidvisionify on 2010-08-30
*bumpity*

Please, anyone?

---

### Post by vidvisionify on 2010-09-01
*shove*

**Please!?**

---

### Post by lidex on 2010-09-03
How about chocolate chip, butter recipe with walnuts? =P~

Try this please.
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv5 enable_msi=1 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by vidvisionify on 2010-09-03
Houston! We have static!

And that's it. :|

---

### Post by lidex on 2010-09-05
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

### Post by vidvisionify on 2010-09-05
All I get is static from the mic. :(

---

### Post by balak on 2010-09-05
I am also seeing the same issue - mic not working. I thought I got the microphone to work in jaunty/karmic, buts its again gone out after lucid update. This is the wife's laptop and heard her complaining today so came to investigate. 

After adding the changes to alsa-base.conf and fixing up the alsamixer, I now get clean static (white noise) when i try recording something with sound recorder.

I am quite familiar with ubuntu so let me know if you need any other debug info. Thanks in advance!

---

### Post by lidex on 2010-09-06
You may need to change the mic selection in your mixer/sound preferences. Also make sure the input of your profile is analog/analog duplex.

---

### Post by pollixx on 2011-02-03
I had the static noise on my dv4.  What I did was lowered the Capture volume to 1/2 in ALSA Mixer and it works perfectly.

Thanks to everyone here in this thread.  I was having problems with my mic, I followed the directions, and figured I needed to lower the volume to 1/2.  GREAT WORK!

---

