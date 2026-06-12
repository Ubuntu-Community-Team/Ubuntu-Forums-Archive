---
title: "Help with input sound please"
date: 2010-06-05
forum: Multimedia Software
---

### Post by uMany on 2010-06-05
Hi,

I had have this problem since I first install Karmic back in February. Now I installed 10.04 and the problem with the input sound is still here.
Plain simple: there is no input sound at all.
I already checked the alsamixer controls at the terminal and everything seems normal.
I have a sonny Vaio laptop model VPCF11FD.
Thanks in advance.

---

### Post by lidex on 2010-06-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by uMany on 2010-06-05
Hi Mr. Lidex
Here is the information. Thanks again.
uname -a
Linux umany 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC275 Analog [ALC275 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC275 Digital [ALC275 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC275

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia GT21x HDMI

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia GT21x HDMI

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia GT21x HDMI

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia GT21x HDMI

---

### Post by lidex on 2010-06-05
Can I get this one too please:
```
sudo lshw -C Sound
```

---

### Post by uMany on 2010-06-05
Of course!
sudo lshw -C Sound
  *-multimedia            
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:16 memory:e3080000-e3083fff
  *-multimedia
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:36 memory:e8e00000-e8e03fff

---

### Post by lidex on 2010-06-05
Missed one;
```
cat /proc/asound/version

```

---

### Post by uMany on 2010-06-05
True, here it is

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 16 2010 for kernel 2.6.32-22-generic (SMP).

---

### Post by lidex on 2010-06-05
That all seems OK. First, for mic problem, check this.
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

Then use pulseaudio volume control (pavucontrol) to select your mic in 'Input Devices' tab.

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

### Post by uMany on 2010-06-06
Thanks mister Lidex but nothing happen :-(
Here some screenshots

---

### Post by lidex on 2010-06-06
Unlink the sliders for the microphone and move one all the way down - it's a mono device.

---

### Post by uMany on 2010-06-08
Mr. Lidex,

Nothing happen.
Any other idea?
I'm really needing to get some sound recorded directly to my laptop :-(
Thanks for your time and concern

---

