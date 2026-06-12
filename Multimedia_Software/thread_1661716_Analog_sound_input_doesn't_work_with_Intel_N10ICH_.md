---
title: "Analog sound input doesn't work with Intel N10/ICH 7 on Ubuntu 10.04"
date: 2011-01-07
forum: Multimedia Software
---

### Post by El Potro on 2011-01-07
Hello Ubuntu community,

I recently upgraded to 10.04 and I haven't stopped having problems.

My sound card is the on-board **Intel N10/ICH 7**

```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

```

And it isn't working alright. I can't use microphone or line-in at all. Sound playback works good though. I'm really upset because I can't figure out how to fix this. Seems it is impossible! But on the contrary, on Win XP, as always, works like a charm.

I really don't know what to do, honestly, and I'm not an idiot. I have noticed that all the gnome configuration panels have changed and seems now they are a lot more simplified. It doesn't matter if I choose between **Line In, Microphone 1 and Microphone 2** (by the way, there is only one microphone plug, so I don't understand why Ubuntu is giving me a second Microphone choice).

I have opened *alsamixer* and all the volume bars are up to the top. I haven't a clue here... Can anyone tell me what can I try to fix this? Anything is welcome. 

Thank you very much.

---

### Post by lidex on 2011-01-07
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by El Potro on 2011-01-07
Thank you very much, here it is [http://www.alsa-project.org/db/?f=6d56d1d91a13fa8e81dcea9e4402e1684046c7f0](http://www.alsa-project.org/db/?f=6d56d1d91a13fa8e81dcea9e4402e1684046c7f0)

---

### Post by lidex on 2011-01-07
You have an older version of alsa. The easiest way to update is using the ppa. Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
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

### Post by lidex on 2011-01-07
If that doesn't help, next do this. ```
echo "options snd-hda-intel model=3stack-6ch" | sudo tee -a /etc/modprobe.d/alsa-base.conf
```
**Reboot**

---

### Post by El Potro on 2011-01-07
First I want to thank you for all the directions you gave **lidex**, but I haven't got good news. It is the same. I have followed all the procedures and nothing. Whether I choose Line-In, Mic or Front Mic, it is all the same. I get no sound at the recorder, or minimum noises (static charge maybe), but nothing more. Take a look at the image of alsamixer.

Honestly, I don't know how to configure it maybe. But in previous Ubuntu releases (I have been using it since Edgy Eft) though it was complicated to set up the microphone, it was possible. Here I'm left with nothing to do.

Anybody could throw me a life preserver? Thank a lot!

---

### Post by lidex on 2011-01-07
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

### Post by El Potro on 2011-01-08
Hi, thank you very much for helping **lidex**

I found the solution to the problem, it was just switching between 6ch to 2ch in alsamixer. That magically activates microphone and line-in. (line-out was already working).

Thank you for your help ;-)

---

### Post by lidex on 2011-01-08
Glad you got it working. 6-channel mode must reconfigure the inputs as outs.

---

### Post by drever on 2011-01-12
Hello Ubuntu Community,

I have the same problem and tried the solutions suggested here. But it did not work out. The alsa report is here: [http://www.alsa-project.org/db/?f=d0c646e2374eeea67464f286391fd7c5e8f6062c](http://www.alsa-project.org/db/?f=d0c646e2374eeea67464f286391fd7c5e8f6062c)

Can anyone help, please? Thank you very much,

Johannes

---

