---
title: "Nvidia HDMI audio detected by alsa, but not by pulseaudio"
date: 2013-04-25
forum: Multimedia Software
---

### Post by odror on 2013-04-25
OS: Ubuntu 13.04
Video card: Nvidia GT 440

alsa clearly identifies the nvidia audio.
But when looking at system-settings -> sound

The nvidia audio is not mentioned and thus cannot be selected. Is there any way to fix that. When I installed 13.04 initially I used an older nvidia card that does not support sound. Then I replaced the card. Can this be the problem. Do I need to re-install 13.04. I tried reinstalling paulseaudio. It did not help.


aplay -l :
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


aplay -L :
> null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=Intel
    HDA Intel, STAC92xx Analog
    Default Audio Device
sysdefault:CARD=Intel
    HDA Intel, STAC92xx Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, STAC92xx Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, STAC92xx Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, STAC92xx Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, STAC92xx Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions


lspci | grep NV :
> 01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 440] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)


---

### Post by pogenwurst on 2013-04-25
I have exactly the same problem with a different Nvidia card.

This is in my syslog:

```
Apr 25 19:18:12 the-english-patient pulseaudio[2848]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Apr 25 19:18:12 the-english-patient pulseaudio[2848]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="pci-0000_05_00.1" card_name="alsa_card.pci-0000_05_00.1" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1""): initialization failed.

```

I've attached the various relevant command outputs.

---

### Post by fullinterest on 2013-04-26
I have the same problem too, but I have noticed that gnome-alsamixer crash when opening, it might mean there's a problem with alsa, as your pulseaudio fail to load an alsa module.

---

### Post by fullinterest on 2013-04-26
The 3 ones like odror if it help.

aplay -l :
> **** Liste des Périphériques Matériels PLAYBACK ****
carte 0: NVidia [HDA NVidia], périphérique 0: ALC1200 Analog [ALC1200 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: NVidia [HDA NVidia], périphérique 1: ALC1200 Digital [ALC1200 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: CMI8738 [C-Media CMI8738], périphérique 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: CMI8738 [C-Media CMI8738], périphérique 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: CMI8738 [C-Media CMI8738], périphérique 2: CMI8738-MC6 [C-Media PCI IEC958]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 2: Headset [Logitech USB Headset], périphérique 0: USB Audio [USB Audio]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 3: NVidia_1 [HDA NVidia], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 3: NVidia_1 [HDA NVidia], périphérique 7: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 3: NVidia_1 [HDA NVidia], périphérique 8: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 3: NVidia_1 [HDA NVidia], périphérique 9: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1

aplay -L :
> default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=NVidia
    HDA NVidia, ALC1200 Analog
    Default Audio Device
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
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC1200 Digital
    Hardware device with all software conversions
sysdefault:CARD=CMI8738
    C-Media CMI8738, C-Media PCI DAC/ADC
    Default Audio Device
front:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Front speakers
rear:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    Rear speakers
surround40:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI 2nd DAC
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Direct sample mixing device
dmix:CARD=CMI8738,DEV=1
    C-Media CMI8738, C-Media PCI 2nd DAC
    Direct sample mixing device
dmix:CARD=CMI8738,DEV=2
    C-Media CMI8738, C-Media PCI IEC958
    Direct sample mixing device
dsnoop:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Direct sample snooping device
dsnoop:CARD=CMI8738,DEV=1
    C-Media CMI8738, C-Media PCI 2nd DAC
    Direct sample snooping device
dsnoop:CARD=CMI8738,DEV=2
    C-Media CMI8738, C-Media PCI IEC958
    Direct sample snooping device
hw:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Direct hardware device without any conversions
hw:CARD=CMI8738,DEV=1
    C-Media CMI8738, C-Media PCI 2nd DAC
    Direct hardware device without any conversions
hw:CARD=CMI8738,DEV=2
    C-Media CMI8738, C-Media PCI IEC958
    Direct hardware device without any conversions
plughw:CARD=CMI8738,DEV=0
    C-Media CMI8738, C-Media PCI DAC/ADC
    Hardware device with all software conversions
plughw:CARD=CMI8738,DEV=1
    C-Media CMI8738, C-Media PCI 2nd DAC
    Hardware device with all software conversions
plughw:CARD=CMI8738,DEV=2
    C-Media CMI8738, C-Media PCI IEC958
    Hardware device with all software conversions
sysdefault:CARD=Headset
    Logitech USB Headset, USB Audio
    Default Audio Device
front:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    Front speakers
surround40:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    Direct sample mixing device
dsnoop:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    Direct sample snooping device
hw:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    Direct hardware device without any conversions
plughw:CARD=Headset,DEV=0
    Logitech USB Headset, USB Audio
    Hardware device with all software conversions
hdmi:CARD=NVidia_1,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia_1,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia_1,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia_1,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia_1,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia_1,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia_1,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia_1,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia_1,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia_1,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia_1,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia_1,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia_1,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia_1,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia_1,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia_1,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia_1,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia_1,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia_1,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia_1,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

lspci | grep NV :
> 00:00.0 Host bridge: NVIDIA Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: NVIDIA Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: NVIDIA Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: NVIDIA Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: NVIDIA Corporation MCP79 Co-processor (rev b1)
00:04.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB controller: NVIDIA Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB controller: NVIDIA Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: NVIDIA Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: NVIDIA Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: NVIDIA Corporation MCP79 Ethernet (rev b1)
00:0b.0 RAID bus controller: NVIDIA Corporation MCP79 RAID Controller (rev b1)
00:0c.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: NVIDIA Corporation MCP79 PCI Express Bridge (rev b1)
02:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 430] (rev a1)
02:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)

---

### Post by ntropia on 2013-04-28
The same problem has been reported in a [Kubuntu forum]("http://www.kubuntuforums.net/showthread.php?62540-13-04-startup-crashes-and-no-HDMI-sound-on-NVIDIA").
There should be an error message in the dmesg output, containing the text "patch_generic_hdmi" and that seem to be triggered when using the configuration that worked on 12.10.

A bug report would be probably appropriate, although, I have no idea on what's the package involved.
Advices are welcome.

---

### Post by ntropia on 2013-04-29
A [bug report]("https://bugs.launchpad.net/bugs/1173769") has been filed by user Landeel from the Kubuntu forum mentioned above.
The bug seems to be related to the 3.8 kernel, and in fact, installing a 3.9 version from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) fixed the problem..

eNjoy

---

### Post by fullinterest on 2013-04-29
> **ntropia said:**
> A [bug report]("https://bugs.launchpad.net/bugs/1173769") has been filed by user Landeel from the Kubuntu forum mentioned above.
The bug seems to be related to the 3.8 kernel, and in fact, installing a 3.9 version from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) fixed the problem..

eNjoy

The installation of the kernel 3.8.9 fail, for me. The 3.9 work well?

---

### Post by SJR Dorset on 2013-04-29
I fixed my HDMI audio problems by installing Kernel 3.8.8 using the following method:
[URL="http://blog-darryldias.rhcloud.com/tag/debian-kernel/"]

http://blog-darryldias.rhcloud.com/tag/debian-kernel/[/URL]

---

### Post by fullinterest on 2013-04-29
I think I'm gonna try the 3.9, I don't want to use unofficial installation, as the kernel ppa provide debian packages

---

### Post by odror on 2013-04-29
I have just downgraded to kernel 3.8.0-17.  It works  now. I hope that the next version will be released with a fix.

---

### Post by fullinterest on 2013-04-29
> **odror said:**
> I have just downgraded to kernel 3.8.0-17.  It works  now. I hope that the next version will be released with a fix.

If you want, there's another way, the way I did. Adding manually quantal repos to install the 3.5 kernel, just choose at startup the 3.5 kernel

---

### Post by fullinterest on 2013-04-29
> **SJR Dorset said:**
> I fixed my HDMI audio problems by installing Kernel 3.8.8 using the following method:
[URL="http://blog-darryldias.rhcloud.com/tag/debian-kernel/"]

http://blog-darryldias.rhcloud.com/tag/debian-kernel/[/URL]

It doesn't work for me, problem with grub

---

### Post by conradin on 2013-04-29
I too am having this issue.
I just upgraded my GPU from a radeon 4650 to a NVidia geForce gtx460, with manufacturers drivers.
With the old card, the sound worked fine.
Now that my GPU is installed, sound wont work.
I blacklisted some nouvo and generic drivers. shown below from vim /etc/modprobe.d/nvidia-graphics-drivers.conf
```

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
blacklist nvidia-current
blacklist nvidia-173-updates
blacklist nvidia-96-updates
alias nvidia nvidia_current_updates
alias nouveau off
alias lbm-nouveau off

```

I am goign to try tooling with the black list, to get my sound back

---

### Post by odror on 2013-04-29
3.8.0-17 comes with the Beta version of 13.04. I was already installed. I had to change the default boot kernel. I would like to be as close as possible to the 13.04 distribution.

---

### Post by conradin on 2013-04-29
Using that "3.8.8" kernel didnt help me at all. In fact is that thing even legit? No idea, i removed it and went back to 3.8.0-19-generic kernel
I tried  installing the nouvo firmware, and enabling the black listed modules, from the 3.8.8 kernel. That made things very bad, almost ususable. 
I re blacklisted the modules, and purged the 3.8.8 kernel.
Then I noted that in the lightdm, my sound was muted. Im using mate / unity, both of which arnt muted in the OS after loged in. 
At this point I have no idea, but the sound is working now. There seems to be some discrepancy between the login volume, and the session volume control.
I can't prove that yet.

---

### Post by melal on 2013-05-11
The best way to solve the problem "Nvidia HDMI audio detected by alsa, but not by pulseaudio" is to install latest ALSA from "ALSA daily build snapshots" for raring: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)
Everybody can try this way I have described: [http://ubuntuforums.org/showthread.php?t=2135049&p=12634757#post12634757](http://ubuntuforums.org/showthread.php?t=2135049&p=12634757#post12634757)

---

### Post by semidog on 2013-05-12
> **melal said:**
> The best way to solve the problem "Nvidia HDMI audio detected by alsa, but not by pulseaudio" is to install latest ALSA from "ALSA daily build snapshots" for raring: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)
Everybody can try this way I have described: [http://ubuntuforums.org/showthread.php?t=2135049&p=12634757#post12634757](http://ubuntuforums.org/showthread.php?t=2135049&p=12634757#post12634757)

Thank you for this! It worked for me running 13.04 with a NVidia GTX 560ti card. Pulseaudio was detecting only the on-board card (also an NVidia). After upgrading ALSA, all is good.

---

### Post by Richard1098 on 2013-05-17
Tried the above, and still don't have HDMI sound via my nVidia GT610.

---

### Post by rolo2 on 2013-07-31
Worked with my GT420 on 13.04.  Thanks!!

> **melal said:**
> The best way to solve the problem "Nvidia HDMI audio detected by alsa, but not by pulseaudio" is to install latest ALSA from "ALSA daily build snapshots" for raring: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+packages)
Everybody can try this way I have described: [http://ubuntuforums.org/showthread.php?t=2135049&p=12634757#post12634757](http://ubuntuforums.org/showthread.php?t=2135049&p=12634757#post12634757)

---

### Post by maxter on 2013-09-08
This also worked for me with a nvdia gt210
Many Thanks!!

---

