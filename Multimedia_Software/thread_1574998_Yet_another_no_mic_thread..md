---
title: "Yet another no mic thread."
date: 2010-09-15
forum: Multimedia Software
---

### Post by cespinal on 2010-09-15
Hello everyone!, 

I have also run in a thought-gone problem since my latest updates: Mic microphone is not working. 

Sound works okay, alsamixer seems to be well configured, no microphones are muted in the sound preferences, and I still can't get it to work. By using the sound recorder, I can tell there is a little feedback when recording, but I can hear nothing playing back such recording. Skype is also useless. 

The output of my Alsa information script is here: [http://www.alsa-project.org/db/?f=0b412d6eb1f6698994ff10dbac2cafe8d3b0b5a7]("http://www.alsa-project.org/db/?f=0b412d6eb1f6698994ff10dbac2cafe8d3b0b5a7")

I have seen many cases like this being solved. Maybe I could get lucky as well? 
Thanks for any hints you may provide. 
Cheers!

---

### Post by halj32 on 2010-09-15
have you checked in your sound preferences that your sound card is set for 1 input & 1 output & the volume on the input is turned up??

---

### Post by jamessimo on 2010-09-15
Also have you allowed Audio Adapter to have (1 Input Mono Input)

I spent hours trying to get a mic when I just enabled this out of desperation and it worked!

---

### Post by cespinal on 2010-09-15
yes halj, sound settings are just like that. 

jamessimo, could you be a little more detailed in that, please? I don't know which one is the Audio Adapter :s

---

### Post by jamessimo on 2010-09-15
Sound Preferences > Hardware and make sure allowed Audio Adapter to have (1 Input Mono Input)

---

### Post by cespinal on 2010-09-16
thanks James....but nothing yet.... 

Remember the mic is detected, and still responds to recordings, but at VERY LOW, useless levels and quality...

---

### Post by lidex on 2010-09-17
I would recommend wiping out the entry to alsa-base.conf that you added and replacing with this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
Now reboot and report results.
Where are you getting the dv9 model from? I have not seen that.

---

### Post by cespinal on 2010-10-09
> **lidex said:**
> I would recommend wiping out the entry to alsa-base.conf that you added and replacing with this:
```
options snd-hda-intel model=laptop position_fix=1 enable=yes
```
Now reboot and report results.
Where are you getting the dv9 model from? I have not seen that.

Hi!. Sorry for the long absence... just moved to another country! lol... changes. 

Thanks for your answer, but this did not work. I made a fresh install of Mint xfce, changed the line as you suggested. but Im still stuck in the same place. 

Here is my new output from Alsa Information Script... .

---

### Post by lidex on 2010-10-09
It may be easiest for you just to install the linuxant driver:
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

Remove that line from alsa-base.conf first.

---

### Post by cespinal on 2010-10-09
> **lidex said:**
> It may be easiest for you just to install the linuxant driver:
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

Remove that line from alsa-base.conf first.

Done... what should I do next? Still have no sound.... :(

---

### Post by lidex on 2010-10-09
> **cespinal said:**
> Done... what should I do next? Still have no sound.... :(

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

### Post by cespinal on 2010-10-09
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

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:

Thank you for taking the time to answer my posts. I really appeciate. 

Still does not work... I have tried those suggestion before if I can remember well. 

I'm starting to consider the fact that my mic might be physically damaged :S....

---

### Post by lidex on 2010-10-10
Could really use your alsa-info output. Can you post the link?

---

### Post by cespinal on 2010-10-11
here it is!! 

[http://www.alsa-project.org/db/?f=a5d4587c9a2a0ba94c373f3f18316aa3ea121da4](http://www.alsa-project.org/db/?f=a5d4587c9a2a0ba94c373f3f18316aa3ea121da4)

---

### Post by lidex on 2010-10-11
Your driver update did not take:
```
!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    
Utilities version:  1.0.22

```
If you installed the linuxant driver, remove it. Also remove the alsa-base.conf entry. Now install build-essential:
```
sudo aptitude install build-essential
```
Next use the alsa-upgrade link in my sig to get full 1.0.23 version. From what I can see your laptop should work with that.

---

### Post by cespinal on 2010-10-12
I thank you for taking the time to help me with this. Still nothing. Sound recorder for example will show some tiny feedback... but no sound at all at playback. 
Here is again the latest alsa info: [http://www.alsa-project.org/db/?f=3a72311a607252f0ea87f83900939c783398b426](http://www.alsa-project.org/db/?f=3a72311a607252f0ea87f83900939c783398b426)

Running the ubuntu sound bug script tells me there is problem in alsa-base :(

Thanks again for everything.

---

### Post by cespinal on 2010-10-12
Quick comment... Reading my dmesg output found this: 
[   19.040159] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
[   19.040275] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input10

Could this be the problem? two mics?

---

### Post by cespinal on 2010-10-14
bumpity?

---

### Post by lidex on 2010-10-14
> **cespinal said:**
> Quick comment... Reading my dmesg output found this: 
[   19.040159] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input9
[   19.040275] input: HDA NVidia Mic as /devices/pci0000:00/0000:00:07.0/sound/card0/input10

Could this be the problem? two mics?

Probably not, as most have an internal and external mic input. 
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

### Post by cespinal on 2010-10-14
I have done all that before with no success. In the attached screenshot, you can actually see that all channels have been enabled in alsamixer, pavu control is set up as suggested and the sound preferences are set up as well. 

As you can see in the sound recorder window. The feedback bar stays in that level no matter what I do.

---

### Post by lidex on 2010-10-14
> **cespinal said:**
> I thank you for taking the time to help me with this. Still nothing. Sound recorder for example will show some tiny feedback... but no sound at all at playback. 
Here is again the latest alsa info: [http://www.alsa-project.org/db/?f=3a72311a607252f0ea87f83900939c783398b426](http://www.alsa-project.org/db/?f=3a72311a607252f0ea87f83900939c783398b426)

Running the ubuntu sound bug script tells me there is problem in alsa-base :(

Thanks again for everything.

Can you provide any details and did you file a bug report?

---

### Post by cespinal on 2010-10-14
I just ran the ubuntu-bug command and the output was ''problem in alsa-base''. And not, I have not filed a bug report...just considered this should be very common. 

Out of my desperation, made a fresh install on kubuntu 10.10... problem persists...

---

### Post by lidex on 2010-10-15
What is this module:
> michael_mic


According to your alsa-info, you have three mics and three mic switches. All switches set to 'on'. Three stereo mic volume controls maxxed out. Try reducing the right channel levels on all three to zero.

What is this output:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by cespinal on 2010-10-15
> **lidex said:**
> What is this module:


According to your alsa-info, you have three mics and three mic switches. All switches set to 'on'. Three stereo mic volume controls maxxed out. Try reducing the right channel levels on all three to zero.

What is this output:
```
cat /etc/modprobe.d/alsa-base.conf
```


There you go :) 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

---

