---
title: "No sound with ubuntu server 10.10 - Have read guide"
date: 2011-03-06
forum: Multimedia Software
---

### Post by Sara_L on 2011-03-06
HI I installed alsa for playback useing( I believe):

sudo apt-get install alsa

lspci reports:
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)


aplay -l reports:
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

At first, before I rebooted, alsa reported it coupldnt find anything, following a reboot, alsamixer came up and i unmuted
the appropriate channels (Master,PCM) and brought the levels up

aplay played out a wav file i had, yet I get no sound from eithor aplay or Audacious (playing via x11 forward)

What am i doing wrong? Ive tried unmuteing/muteing various other channels in alsamixer (most notably S/PDIF) yet nothing seems to work. 


When i had ubuntu desktop installed, everything worked fine, and in XP it works as well, so I've ruled out a hardware issue.

Thanks

---

### Post by lidex on 2011-03-06
Try this in a terminal:
```
gstreamer-properties
```
and set your defaults to alsa.

---

### Post by Sara_L on 2011-03-07
Thanks for the reply. I tried it, and its not installed. It appears to be part of Gnome, which shouldn't be needed as there is no gnome on this system, or even an X-server...

My only hope is to reinstall desktop from scrach, and hopefully find out what server did wrong, but desktop did right

---

### Post by lidex on 2011-03-07
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by ykanello on 2011-12-21
Hi,
not to be an a-hole, but why do you install Alsa?
ubuntu 10.10 that I saw on your profile that you have, is using as default PulseAudio. Installing Alsa on top of PulseAudio won't do much. :(
you have to remove all pulseaudio libs and programs and install the alsa.
But then you break the ubuntu-desktop dependencies.
imho is easier to learn to use pulse audio.
But still if you want PA removed and Alsa installed, please post again and we'll find some instructions/guide. (or make one)

---

### Post by lidex on 2011-12-27
> **ykanello said:**
> Hi,
not to be an a-hole, but why do you install Alsa?
ubuntu 10.10 that I saw on your profile that you have, is using as default PulseAudio. Installing Alsa on top of PulseAudio won't do much. :(
you have to remove all pulseaudio libs and programs and install the alsa.
But then you break the ubuntu-desktop dependencies.
imho is easier to learn to use pulse audio.
But still if you want PA removed and Alsa installed, please post again and we'll find some instructions/guide. (or make one)

Hi, not to be an a-hole, but why do you post inaccurate info on an ancient thread?

---

