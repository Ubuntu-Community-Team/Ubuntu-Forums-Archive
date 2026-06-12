---
title: "100% New to Linux"
date: 2013-01-04
forum: Multimedia Software
---

### Post by rwhipps on 2013-01-04
So I have never used anything other than Windows. I decided to install Ubunutu 12.10 and am LOVING it so far. My only qualm so far is I can't get my subwoofer on my Toshiba Qosmio to work. I've searched and I have searched, and have found a few possible fixes, but they have all been for Asus computers so I have not tried them out. I'm still learning the ropes and am afraid to do anything outside of my knowledge. So is there a fix for this? I'm sorry if this has already been asked and I apologize for my n00bness.

---

### Post by papibe on 2013-01-04
Hi rwhipps. Welcome to the forums ):P

Could you post the results of these commands?
```
aplay -l

aplay -L
```
Regards.

---

### Post by rwhipps on 2013-01-04
Thanks for the welcome, I sure can...

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: ALC272 Digital [ALC272 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


 
aplay -L

default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, ALC272 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=Intel,DEV=0
    HDA Intel, ALC272 Digital
    HDMI Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=3
    HDA Intel, ALC272 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=3
    HDA Intel, ALC272 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=3
    HDA Intel, ALC272 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC272 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=3
    HDA Intel, ALC272 Digital
    Hardware device with all software conversions


P.S. This is definitely a learning experience haha.

---

### Post by rwhipps on 2013-01-05
Any help?

---

### Post by iMurshaq on 2013-01-05
advice for posting terminal outputs, please put them in code brackets:
```
like this
```

and also please show output from;
lsusb

lspci

P.S. Welcome to the forums!!!

---

### Post by rwhipps on 2013-01-05
Sorry about that. Here's the other codes...

```
ryan@ubuntu:~$ lsusb
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 007 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 008 Device 018: ID 0930:0200 Toshiba Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ryan@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: NVIDIA Corporation G94 [GeForce 9700M GTS] (rev a1)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
14:00.0 Network controller: Intel Corporation WiFi Link 5100
20:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
20:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
20:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
20:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
20:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
```

Thanks for the welcome!

---

### Post by adityamagadi on 2013-01-06
seems like your hardware is detected but not responding ... under system settings goto the sound tab check for your speaker settings.

---

### Post by rwhipps on 2013-01-06
I've tried the speaker settings a few times under system settings, but nothing is select-able. It is set to play sound through speakers, but the only available option I can change is the balance. Fade and subwoofer level are there, but not an available option to tweak.

Also, when I do a sound test only the front speakers are testable.

---

### Post by rwhipps on 2013-01-07
Is there anything I can do to fix this or am I screwed?

---

### Post by iMurshaq on 2013-01-08
I've had similar problems on lubuntu quantal. You can try installing a different sound manager on the software center. Try alsamixer and let me know how it goes

---

### Post by rwhipps on 2013-01-09
Went through alsamixer couldn't find anything to play other speakers.

---

### Post by rwhipps on 2013-01-10
```
pcm.!default {
type plug
slave.pcm “surround51&#8243;
slave.channels 6
route_policy duplicate
}
```

I was able to use this code and it seems that the front/rear speakers are now playing, although I can't really tell if the subwoofer is working. I'm assuming it is, but I still can't adjust its' level.

---

### Post by rwhipps on 2013-01-17
Any help at all?

---

