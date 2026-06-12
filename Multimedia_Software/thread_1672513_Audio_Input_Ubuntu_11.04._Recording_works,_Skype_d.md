---
title: "Audio Input Ubuntu 11.04. Recording works, Skype doesn't"
date: 2011-01-21
forum: Multimedia Software
---

### Post by MAS12 on 2011-01-21
I'm fairly new to Ubuntu, using version 11.04. 

Problem: Audio input does work when I use the sound recorder, but is not recognized in other applications (not in Skype, nor in Sound Preferences or PulseAudio Volume Control)

Other info: Hardware is Analog Stereo Duplex. Input volume is at max, not muted. Microphone is the normal internal one on a Lenovo Ideapad U460

Anyone know how to solve this? Thank you!!

---

### Post by Bucky Ball on 2011-01-21
Why are you using 11.04??? As a new user, you would be better advised to be using the latest long term support release, 10.04 LTS.

Are you sure you didn't install 10.10 and it is just showing 11.04? This is a known bug at the moment; 11.04 is not released yet and won't be until April 2011. If you are using 11.04 on purpose and you are not wanting a very steep learning curve I would advise you re-install 10.04 LTS.

Welcome to the forums. ;)

---

### Post by MAS12 on 2011-01-21
You're right - [B]System > About tells me 11.04, but it is actually 10.10 (when I ran cat /etc/lsb-release
in the command line I got:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10" )

So...anyone know how to solve this issue on Ubuntu 10.10. Thank you very much!!
[/B].

---

### Post by MAS12 on 2011-01-21
I found this thread [http://ubuntuforums.org/showthread.php?t=1599520](http://ubuntuforums.org/showthread.php?t=1599520) and downloaded Gnome ALSA mixer, which helped - the audio input is now registering at least when I go to sound preferences, but it's garbled on Skype

---

### Post by lidex on 2011-01-21
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

Skype references:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)
[https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)

---

### Post by MAS12 on 2011-01-21
Yay! That worked. Thank you very much for all your help!

---

### Post by lidex on 2011-01-23
You're welcome. Enjoy.

---

### Post by Chuckaluphagus on 2011-05-25
lidex, I just wanted to thank you for this as well.  I was having an identical problem on an install of 11.04 on a new Acer Aspire One netbook, and your instructions solved it perfectly.

---

### Post by MattiGee on 2011-06-14
Thanks a million! I have a new Acer Aspire netbook and am very new to Linux (finally had enough of Windows). Everything was perfect except my Skype. But now that works too, thanks to your instructions! Happy, happy, happy!

---

### Post by Ramblerrr on 2011-08-05
I registered just so I can say thanks - this brought the end to a very frustrating episode.

---

### Post by tj185018 on 2011-08-07
As I am a struggling but satisfied new Linux user scouring the forums down the Rabbit hole, I have to thank you also for the step by step how to fix my mic problem....did not even think about the Microphone being Mono...Thanks agaiin!

---

### Post by andresv on 2011-08-11
Amazing. It works. I wonder why skype has become so frustrating and difficult to configure: every time a new version of ubuntu comes out, reinstalling Skype feels almost like in the mid 1990s, when everything had to be done from scratch.

Thank you for the post!!!

---

### Post by amarendra on 2011-08-20
> **lidex said:**
> First, for mic problem, check this.
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


Skype references:
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)
[https://help.ubuntu.com/community/SkypeTroubleshooting](https://help.ubuntu.com/community/SkypeTroubleshooting)
Worked like a charm. Thanks :-)

---

### Post by alextacy on 2011-08-23
Hi there, 

unfortunately I don't seem to have cracked this.  The input is still totally fuzzy.  I have installed both the Alsa mixer & pulse audio controls, and appear to have some success but then it just goes back to being terrible, especially if I adjust the mic input under "sound preferences" (this resets the right channel input in pulse audio).

Is there anything else I might be doing wrong?  I can't seem to set the levels in Alsa to 50%, they just automatically reset themselves...

other than this i don't have a clue & like many people I sort of depend on skype for calls with clients.

Cheers, 

A

---

### Post by Bucky Ball on 2011-08-23
> **alextacy said:**
> Hi there, 

unfortunately I don't seem to have cracked this. 

You would be better off posting a fresh thread with a descriptive title. Explain your issues there and you will have more success. This thread is very old. ;)

---

### Post by lidex on 2011-08-24
> I can't seem to set the levels in Alsa to 50%, they just automatically reset themselves...
There is a setting in skype to allow control of audio levels - disable it. This has been posted many times.

---

### Post by danielkr on 2011-08-31
> **Ramblerrr said:**
> I registered just so I can say thanks - this brought the end to a very frustrating episode.

Same here.  Was trying to pipe in audio from a 2nd workstation on my desk to my CL SB Fatality so I would only need one set of speakers on my desk.  Everything LOOKED ok in the Sound Preferences...  Also didn't work with the Internal Audio.  

Thanks a ton, 

Daniel

---

### Post by euloiix on 2011-10-17
Thank you :)

---

