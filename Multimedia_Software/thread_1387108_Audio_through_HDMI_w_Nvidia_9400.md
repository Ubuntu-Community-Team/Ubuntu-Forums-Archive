---
title: "Audio through HDMI w/ Nvidia 9400"
date: 2010-01-21
forum: Multimedia Software
---

### Post by Amorget on 2010-01-21
Hi, I am having problems with my Audio through HDMI on my MSI Nvidia 9400 GT.  The motherboard is a Biostar G41 DVI.  I am running Mythbuntu 9.10 with the latest ALSA, as updated by this thread:  [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)   I have unmuted both the IEC958 switches that are in the Mixer.  I have one that is just IEC958 and the other is IEC958 Default PCM and both are unmuted.

I am also running the latest beta Nvidia drivers for the card, as downloaded and installed yesterday.

I have verified by taking the time to install Windows 7 that the cable connecting the SPDIF connector on the motherboard to the video card is installed correctly as I was able to get it working in Windows 7.

Output of /proc/asound/devices
> 0: [ 0]   : control              
1:        : sequencer            
6: [ 0- 2]: hardware dependent    
16: [ 0- 0]: digital audio playback
17: [ 0- 1]: digital audio playback
24: [ 0- 0]: digital audio capture
33:        : timer

Output of cat /proc/asound/card0/codec#* | grep Codec

> Codec: Realtek ALC662 rev1

Output of aplay -l

> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1
Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1
Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Output of aplay -L
> null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC662 rev1 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output

Output of lspci | grep -i audio
> 00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High
Definition Audio Controller (rev 01)

Anyone have any other ideas to get the audio working through HDMI?  It is a HTPC so I would have no problems completely disabling all of the analog output as the only thing it will ever be connected to is a receiver or TV with an HDMI cable.

Also, it is very possible that I just haven't gotta any of the media players to properly use the digital out instead of the analog out.  I have VLC set to use SPDIF when available and I also installed Mplayer and messed around in there with what ALSA out it was using, but never got any sound and produced a lot of errors with invalid combinations.

If there is any more info needed please let me know and I will find it.  This is the only thing that is holding back my amazing awesome HTPC!!

Thanks,
Douglas

---

### Post by Amorget on 2010-01-22
](*,)  Help?

---

### Post by Amorget on 2010-01-26
Bump... still lost on this.

---

### Post by larsolav on 2010-01-26
Not sure if I am much help here, but that is weird, "aplay -L" does not show your HDMI audio at all.
I have an EVGA MB with the 9300 chip and it shows HDMI as an audio option under aplay -L. I used the NVIDIA drivers that Mythbuntu installed (not sure what version that is), and at least get sound on my recordings (and sometimes music, but more about that in another thread to come this weekend...). Are you sure the Nvidia drivers are correctly installed?

---

### Post by Amorget on 2010-01-26
Is your Nvidia card built into the motherboard?  My card is a PCI-Express card, which for audio just uses the SPDIF on the motherboard to pass the sound through.  For that reason I don't think it is unexpected to not see HDMI as an audio option.

As far as the drivers being installed correctly, I believe they are.  The nvidia-settings indicates I am using the correct drivers and I have an Nvidia splash screen indicating I am using the Beta driver.

---

### Post by dvinothkumar on 2010-10-05
Amorget, I am facing the same issue with MSI gt9400. I don't see the HDMI listed in aplay -L. And audio is not working through HDMI. Were you able to resolve this issue?

---

### Post by Amorget on 2010-10-05
Ok, first things first:

Do you have a SPDIF cable run from your motherboard/sound card to the video card?

You won't see a HDMI audio option in aplay because of the way the Nvidia 9xxx series does HDMI audio, at least with the stand alone cards.

---

### Post by xavhornet on 2010-12-18
Hello, i am in the same trouble that you wit an 9400GT. I am try to install an windows 7 to see if my cable between my spdif and my video card is god.
Do you have new issue about that. like you i can not see any HDMI Audio from my nvidia card with the last driver. I think the trouble come from here??

Thank you

---

### Post by VietCanada on 2010-12-18
I had that problem. I'm trying to remember how I solved it. If I remember correctly I went into Bios and changed HD sound to AC sound. I also found a PPA for Ubuntu audio dev somewhere. But I'm pretty sure going the bios route solved the problem immediately.

---

### Post by Amorget on 2010-12-18
Mine stopped working so I gave up and put in a stand alone sound card with digital out.  I am not sure what broke on mine as I tried a clean 10.04 install and it didn't fix my problem.

---

### Post by xavhornet on 2010-12-19
Hello thank you for yours informations.
I put a Seven, it detect only my spdif (if i play music seven show me vibration, like sound work). I install the last Nvidia driver and it let me choose HDMI with audio. I put my hdmi cable in my TV but no sound..Damm..:(

I don't give up..

---

### Post by xavhornet on 2010-12-21
I search in forums, and i ask me if it isnt alsa who do not see the audio hdmi port in the 9400gt. If found one where some one patch the "patch_nhdmi.c" file to add the ID of is card and after aplay -l make see it.

---

