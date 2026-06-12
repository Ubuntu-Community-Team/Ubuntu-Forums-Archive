---
title: "Mic not working, Cheese not recording, and sound recorder not recording. Acer"
date: 2011-02-27
forum: Multimedia Software
---

### Post by Hcamez on 2011-02-27
Hi

- I tried to use skype today but my mic was not working (i checked all levels and made sure not muted).

- So I decided to test it with Sound Recorder - it would not even attempt to record it.

- Then I tied to test it using Cheese - It too would not record (web cam was working but as soon as I hit record it froze with a split image of whatever the camera was looking at when I hit record) - There was nothing to play back.

I have searched a lot of forums and googled it and found a lot of people are having similar problems - but no one seems to have ANY answers.

Please, if anyone has any suggestions that would be fantastic.

My computer is an Acer ASPIRE 4540 with a built in mic and a built in crystal eye webcam.


I have tried a number of different programs but nothing works - the only program i could use to test the mic was Skype. No other way of testing. i even installed the crystal eye program in wine - it wouldn't even run.

I like Ubuntu and what its all about, so I would rather not revert back to Windows.

Thanks

---

### Post by Hcamez on 2011-02-27
Now sound is not working either :(

computer is deaf and dumb

---

### Post by Hcamez on 2011-02-28
I still have to figure out how to get my sound working again, but I have the mic working.

The instructions in this link worked just fine (It seems).

[http://ubuntuforums.org/showthread.php?t=1696587](http://ubuntuforums.org/showthread.php?t=1696587)

---

### Post by lidex on 2011-03-01
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by atentik on 2011-03-11
> **Hcamez said:**
> I still have to figure out how to get my sound working again, but I have the mic working.

The instructions in this link worked just fine (It seems).

[http://ubuntuforums.org/showthread.php?t=1696587](http://ubuntuforums.org/showthread.php?t=1696587)

I am having the same issue you had with your mic. I followed the link and tried instruction but my mic still does not work. Here is what I did.

I added ```
*options snd-hda-intel position_fix**=1 model**=laptop*
``` to my ```
sudo gedit /etc/modprobe.d/alsa-base.conf
``` where laptop for my machine is a thinkpad so I added thinkpad but still the mic problem was not solved. 

I noticed there are 2 equal signs in the code... is it supposed to be that way? also, is putting just thinkpad enough or do I need to put something else.

Here is my Alsa information in case you need it: [ALSA]("http://www.alsa-project.org/db/?f=c3a8f0f79ca46217d856ce875631c9f7be6ef59f")

---

### Post by lidex on 2011-03-17
@atentik
Try narrowing down your alsa-base.conf edits to this alone:
```
options snd-hda-intel model=thinkpad
```
Also remove the conflicting entry of *model=3stack*
Reboot.
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

