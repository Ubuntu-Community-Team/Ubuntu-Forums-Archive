---
title: "Microphone systems not working at all."
date: 2010-07-21
forum: Multimedia Software
---

### Post by accurate270 on 2010-07-21
Hi,
I want to use my webcam to do some VoIP (or any microphone) but I'm having troubles.  Over the VoIP (or any other system) I can hear everything perfectly.  BUT voice will not record, resulting in no one being able to hear me.

I've looked at the following site...
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
which lead me also to...
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

I have done everything in the Blog mentioned above.
Then I continued in the ubuntu help- but in "step 3" It does not give me anything like what it says it should. (or maybe it does and I just don't know how to read it.)

I've tried everything I know how to do.  I have only had Ubuntu for a month and am still getting use to the system and have limited knowledge with programming etc.

This might be important-- I'm running 10.04.
I have a Dell XPS (~2006)
I have a Creative Live! Cam Notebook Pro Webcam 
([http://us.store.creative.com/Live-Cam-Notebook-Pro-VF0400-BStock/M/B001LK6VZQ.htm](http://us.store.creative.com/Live-Cam-Notebook-Pro-VF0400-BStock/M/B001LK6VZQ.htm))


I hope someone can help me!

Have a great day

---

### Post by lidex on 2010-07-23
Do you get microphone input with sound recorder?
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

### Post by ths64 on 2010-07-23
I got the opposite problem, the mic turn on all the time.  I've tried to set it to "off" unless activated by a program, but very often it is allways on.  Yesterday i allmost blow my ears of when it went in to an imerse feed-back loop on my laptop.  My ears still hurts-----

---

