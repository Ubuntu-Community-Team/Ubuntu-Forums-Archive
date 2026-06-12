---
title: "Lost HDMI audio after upgrade to 10.04"
date: 2010-06-19
forum: Mythbuntu
---

### Post by korgman on 2010-06-19
I've had audio working over HDMI for over a year.  Today, I upgraded my mythbuntu distro to 10.04 and I have lost all audio.  I'm using HDMI.

It finds the device

```
matt@mythtv:/etc$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


matt@mythtv:/etc$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
matt@mythtv:/etc$ 


```

I get no sound when I run this:

```
matt@mythtv:/etc$ speaker-test -Dhdmi:NVidia -c6 -twavq

speaker-test 1.0.22

Playback device is hdmi:NVidia
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right


```
I ran the alsa config script and my alsa settings are all loaded and visible at this link:
[COLOR="Blue"][http://www.alsa-project.org/db/?f=e4daf11d561ff9501b9b7c1f352e511ec05042bb](http://www.alsa-project.org/db/?f=e4daf11d561ff9501b9b7c1f352e511ec05042bb)
[/COLOR]
Is there something wrong with nvidia drivers?  I notice that the "Hardware Drivers" app doesn't list the version of the installed nvidia driver.  It used to say NVIDIA accelerated graphics driver (version 185).  Now it says (version current[Recommended])

---

### Post by goffa72 on 2010-06-19
Hi Korgman

One thing that caught me out after upgrading was that the HDMI output was muted. Have you ran alsamixer to unmute the output?

---

### Post by korgman on 2010-06-19
I don't have a HDMI on/off in alsamixer.  I do have:
S/PDIF,  S/PDIF D, S/PDIF 1, Channel, <hdmi_vol> 
All of which are unmuted, channel is set to 6ch, and hdmi_vol is set to 100.

---

### Post by goffa72 on 2010-06-20
One or more of S/PDIF,  S/PDIF D, S/PDIF 1 is for HDMI I have them all unmuted in alsamixer, Channel is also at 6 but don't have a <hdmi_vol> in F3: playback view. MY HDMI audio worked with minimal fuss with fresh install of 10.04, just had to unmute S/PDIF,  S/PDIF D, S/PDIF 1. 

My alsa version is 1.0.22 and nvidia is 195.36.15

---

### Post by korgman on 2010-06-20
This problem is bigger than I thought.  I have no audio out of the analog outputs either.  Now, I'm entering panic mode.

---

### Post by DraikX on 2010-06-20
This is a fresh install of Kubuntu 10.04 for me and I only have audio coming from startup, shutdown, and Amarok. I do not have audio playing with VLC, Firefox, or Kaffeine. I've been through many forums, but none seem to be the solution for me. I'm on an Eee Box PC EB1501 with the nVidia ION driver. There has to be a setting which is being overlooked as it works fine on VLC in Windows 7 (default OS that came with it).

I don't know if it will be helpful to anyone reading this thread, but I am attaching my package list from "dpkg --get-selections | grep install" in hopes that I'm just missing a package that will resolve the issue.

---

### Post by nickrout on 2010-06-21
I think you should have your sound set to alsa:hdmi in the frontend config.

What do you have it set to?

---

### Post by DraikX on 2010-06-21
> **nickrout said:**
> I think you should have your sound set to alsa:hdmi in the frontend config.

What do you have it set to?

In K Menu > System Settings > Multimedia, I have it set to:
HDA Nvidia (NVIDIA HDMI)

That is the setting for all of the available outputs. That is selected with "show advanced devices" checked.

---

### Post by nickrout on 2010-06-21
> **DraikX said:**
> In K Menu > System Settings > Multimedia, I have it set to:
HDA Nvidia (NVIDIA HDMI)

That is the setting for all of the available outputs. That is selected with "show advanced devices" checked.

read my post FRONTEND config!!!

---

### Post by DraikX on 2010-06-22
I have this issue resolved. Thanks to noaXess in #kubuntu, here is the solution:

```
sudo apt-get install pulseaudio pulseaudio-utils gstreamer0.10-pulseaudio pavucontrol
```

Go to K Menu > System Settings > Multimedia

Choose Pulseaudio as the default audio controller

Restart the computer.

I am now listening to audio playing from both VLC and Firefox, which I was not doing so previously. You are also now controlling the audio level through Pulse Audio Volume Control. I hope this resolves it for you, too.

---

