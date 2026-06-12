---
title: "Problems with 5.1 digital out"
date: 2012-10-16
forum: Multimedia Software
---

### Post by cholten99 on 2012-10-16
I've recently bought a new PC, installed Ubuntu and am now unable to get 5.1 digital sound working. Simple analogue stereo works fine on both the front and rear connectors.

On my old box I connected the coax connection from my soundcard to my surround sound amplifier, set Settings->Sound to "Digital Stereo Duplex" and it worked.

My old soundcard doesn't fit in my new machine so I'm using the build-in sound hardware. I'm connecting the combination output socket on the back of the PC via the same cable to my surround amp as before.

The MB is an MSI Global H61M-P31 with an RealTek ALC887 sound chip.

When I go to Settings->Sound I only see "Headphone Built-in Audio" and "Analogue Output Built-in Audio" - no digitial options.

The output from aplay -l is:

default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC887-VD Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC887-VD Analog
    Hardware device with all software conversions

While googling for ALC887 I've seen some references to "ALC887 -VD Analog" and some to "ALC887 -VD Digital". Does anyone know if I need to force it to chance mode somehow?

Thanks for any help.

---

### Post by smilingfrog on 2012-10-19
I don't know if this will help at all, but I lose surround sound everytime I update a kernel. Currently I am running Linux 2.6.32-43-generic.

There is an old surround sound tutorial [here]("http://ubuntuforums.org/showthread.php?t=795525") that outlines some of the problems with surround. There is a big disclaimer at the top that you don't need to use it anymore, but the information is nice.

I have had to edit my /etc/pulse/daemon.conf file to default for 6 channels instead of two, which sounds like your problem.

Then I have to install header files:
```
sudo apt-get install build-essential linux-headers-2.6.32-43-generic
sudo apt-get install linux-backports-modules-alsa-2.6.32-43-generic
```

For whatever reason, these don't automatically update for me.
Then I reboot, and the system has surround sound again when tested with speaker-test
```
speaker-test -Dplug:surround51 -c6 -l1 -twav

```

I am still running Ubuntu 10.10 because I am lazy. UMMV

---

### Post by BicyclerBoy on 2012-10-19
Those packages don't update because you have not installed the correct meta package that always pulls in the (kernel) matching versions.

The OP wants digital S/PDIF output not 6 channels of analogue.
The default surround5.1 is 6 analogue ch out.
The only way surround5.1 can output digital is if you redefine it to use the AC3 encoder

@OP
Do you have any snd_hda_intel modprobe options in /etc/modprobe.d/*.conf ?

maybe you should try find the alsa info script, run it & post the link.

The script makes output like this:
[http://www.alsa-project.org/db/?f=5dab0c98791e8733e35034a3bb86c16db830317e](http://www.alsa-project.org/db/?f=5dab0c98791e8733e35034a3bb86c16db830317e)

---

### Post by cholten99 on 2012-10-20
Thanks for replying.

No snd_hda_intel options in the modprobe folder.

Alsa script output here : [http://www.alsa-project.org/db/?f=c4231297e125a1c00ebd7521fb5de5af0e407c16](http://www.alsa-project.org/db/?f=c4231297e125a1c00ebd7521fb5de5af0e407c16)

I'd expect the output from aplay -l to be something like:

**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

But instead it's:

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Missing off the digital side completely.

---

### Post by BicyclerBoy on 2012-10-21
I imagine it is possible there is no digital s/pdif output option on the mobo..

Just how new is this hardware ?

Does your PC/laptop have hdmi output connectors ?
Some of the very first hdmi output video cards did not support audio.

But a bigger question is why don't the HDMI audio codecs don't show up..

---

### Post by cholten99 on 2012-10-21
> I imagine it is possible there is no digital s/pdif output 
> option on the mobo.

Well, the MB specs are [here]("http://www.msi.com/product/mb/H61M-P31--G3-.html#/?div=Detail"), not a lot of detail unfortunately. 

> Just how new is this hardware ?

I bought it a couple of months ago.

> But a bigger question is why don't the HDMI audio codecs don't 
> show up.

That was me being dumb I'm afraid. I forget that the HMDI video out I'm using is converted out of the DVI port.

---

### Post by BicyclerBoy on 2012-10-22
Very new iCPU...ivybridge ?

I would guess that you need a very recent kernel to detect/expose the new devices in mobo..

HDMI audio is possible over DVI link. That mobo has DVI-D (okay) & this can connect to hdmi of TV/monitor. HDMI is good to 1920x1200@60Hz.

I would suggest using xorg-edgers ppa (not without some risk) to update the kernel & all graphics components.

The graphics drivers (& HDA audio) for the latest iCPUs is in a state of continuous improvement..

But there is some risk of trouble with bugs & the latest kernel not working with some other packages like wifi drivers etc..

---

### Post by cholten99 on 2012-10-22
If it looks like having to go to a non-standard kernel is needed I'll just shell out for a separate soundcard.

Thanks for the help.

---

### Post by BicyclerBoy on 2012-10-23
The xorg-edgers is not too radical..is only version 3.5..
I don't want to make your system unstable. 

Don't waste a lot of money on a soundcard as hdmi (when working) is superior (if you have hdmi HTAmp)..

I believe "Gamers" find a soundcard useful as you can always get analogue 5.1 sound output to work & you can change the mix.

---

### Post by jocko on 2012-10-24
> **BicyclerBoy said:**
> The xorg-edgers is not too radical..is only version 3.5..
I don't want to make your system unstable. 

Don't waste a lot of money on a soundcard as hdmi (when working) is superior (if you have hdmi HTAmp)..

I believe "Gamers" find a soundcard useful as you can always get analogue 5.1 sound output to work & you can change the mix.
His motherboard does not have any hdmi output, and from the specs and the manual I can't find that it has any s/pdif.
So there are two options for getting digital audio:
1. Get a sound card with s/pdif.
2. Get a graphic card with HDMI.

---

### Post by BicyclerBoy on 2012-10-24
The mobo specs state it supports/compliant with azalia 1.0..

So it it very likely the 3.5mm jacks are analogue & digital with auto pin detection/sensing..
This could be the part of the problem.

There is no reason to think the DVI-D can not support HDA audio when using the iCPU/GPU..
The mobo specs (online) are so vague & marketing focused..

---

