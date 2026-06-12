---
title: "No HDMI sount in Ubuntu 11.04"
date: 2011-05-02
forum: Multimedia Software
---

### Post by DeusX on 2011-05-02
Hi,

I have recently installed Ubuntu 11.04 64bit. After normal install process, it invited me to install ATI proprietary drivers (because I have an ATI Radeon HD4850 video card).

Everything seems to work out of the box, except the HDMI sound. The HDMI video works OK, and also the normal sound using the onboard soundcard work OK.

By my knowledge I think I have setup the audio properties correctly. Some screen-shots attached.
What happens when I switch the output to HDMI is no audio signal on the TV.



Btw, I am a noob and my Ubuntu install is 1st one after years of Windows only. Also, the HDMI works OK (both sound and video) on my Win7 64 bit install.

---

### Post by 4Orbs on 2011-05-02
On my machine I must first disable the onboard sound chip in order to get HDMI audio from the card. Select "Off" in the dropdown profile menu.

---

### Post by gfgodoy on 2011-05-02
On sounds, Click on hardware. Internal audio (not hdmi)
Try to select digital stereo hdmi output on its profiles. 

Mine works (hp pavilion dv5-2050br) but it doesn't show the two devices that you have, good luck.

---

### Post by fercastro on 2011-08-21
Although this is somewhat an old thread, I would like to share something it worked for me.

I installed GNOME-Alsamixer (you can get from Synaptic Package Manager) and ticked IEC958, IEC958 Default PCM and IEC958 (this is no typo, there are two IEC958 options).

Cheers.

---

### Post by therealsybarite on 2011-08-21
hi.  I'm also unable to get sound through HDMI.  I have an HP pavilion dv6000, and i'm trying to get the sound through HDMI to my stereo receiver.  any help will be highly appreciated.

here's my HW as shown in alsamixer:
Card: HDA Intel
Chip: Realtek ALC268

I installed GNOME alsamixer as suggested.  Two options are show, IEC958, IEC958 Default PCM, and both are checked.


checking HW I'm expecting to see INTEL HDMI listed, but it is not there.  Below is all I see:

michal@michal-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


It is also missing from the list of configured sound devices:

michal@michal-laptop:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC268 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC268 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC268 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC268 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC268 Digital
    Hardware device with all software conversions
michal@michal-laptop:~$

---

### Post by psychas on 2011-09-17
Hello everyone. Was there any solution to this? I'm having the same problem getting audio through HDMI. I have an ATI R6XX HDMI sound card. I tried all the suggestions listed in this thread. Nothing seems to work.

---

### Post by BicyclerBoy on 2011-09-17
Post #5 is a laptop with mobo sound &/or using sandybridge or AMD APU for the extra trouble.

Post #6 is some discrete ATI graphics card..are you sure it supports HDA HDMI audio ?
AFAIK You have to run the proprietary video driver to expose the HDMI HDA codecs.

I doubt the problems are the same..the solution could be..

Found this:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/848941](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/848941)

---

### Post by psychas on 2011-09-21
Thanks BicyclerBoy. Yeah that's what I ended up doing. Downloaded ATI's proprietary driver and it worked. Would've done it before but kept reading that it's not advised to use proprietary on Linux. Thanks again.

---

### Post by keishia.tee on 2011-10-09
Hi, I'm having problems with hdmi as well... I'm running 11.04  on a HP G62 and I just got the analogue working. I'm a bit muddled about the meaning of these:

lspci | grep Audio
```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
```

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC270 Analog [ALC270 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L
```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel, HDMI 0
    HDMI Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC270 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=3
    HDA Intel, HDMI 0
    Hardware device with all software conversions
```

Am I missing some kind of hardware?? I would really appreciate a hand, I know its probably obvious but I'm all confused! Thanks!

---

### Post by SamHack on 2011-10-09
I'm a bit of a noob so I'm sorry if this dosen't help but I had this problem. I selected sound preferences from the dropdown sound menu, selected the **Output** tab, changed the device from internal to **High Definition Audio Controller** and under the **Hardware** tab changed the profile Of the HDMI controller to **Digital Stereo (HDMI) nr 2 Output**.

That did it for me.

---

### Post by keishia.tee on 2011-10-09
Thanks for your reply SamHack, but those options don't appear at all for me- I think that's the problem. The only choice I have under output is "Internal Audio Analogue Stereo" and under Hardware is "Internal Audio." Of the option in the dropdown menu on the hardware tab, only Analog stereo duplex and Analog stereo output. 

I have ALSA mixer installed- at the bottom I have checkboxes for IEC958 and "Auto-Mute Mode" and that's it. In other threads I've seen that there should be more than one option here (apart from mute mode), but I'm not sure that I understand what IEC958 actually means... 

Thanks in advance! (blush)

---

### Post by skyviannes on 2011-10-10
> **SamHack said:**
> I'm a bit of a noob so I'm sorry if this dosen't help but I had this problem. I selected sound preferences from the dropdown sound menu, selected the **Output** tab, changed the device from internal to **High Definition Audio Controller** and under the **Hardware** tab changed the profile Of the HDMI controller to **Digital Stereo (HDMI) nr 2 Output**.

That did it for me.

This fixed it for me.  I'm running an Nvidia 550 gt card and using a Vizio HDTV as my monitor.  Hope everyone else figured their issues out too.  Cheers!

---

