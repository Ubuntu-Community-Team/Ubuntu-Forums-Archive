---
title: "Xonar ST Soundcard only initiated correctly after random number of reboots"
date: 2016-08-10
forum: Multimedia Software
---

### Post by percychris1 on 2016-08-10
I have a PC with Ubuntu 16.04 in witch I use both the Gigabyte GA-H97-Gaming 3 onboard Realtek ALC1150 codec (which always gets initialized flawlessly)
and a PCI ASUS Xonar Essence ST with H6 Daughterboard soundcard, which needs a random number of reboots before getting initialized.
Prior, on Ubuntu 14.04 it also occasionally (rarely) happened that I had to reboot once (and only once) before the Xonar got initialized.
When the add in soundcards gets initialized correctly it works until reboot.
When I look at the PCI bus (with lspci) I always see the Soundcard, whether the Xonar PCI card gets initialized or not. 
There are two slight differences when the Xonar gets initialized correctly, Kernel driver in use: snd_virtuoso gets added and IRQ 11 changes to IRQ 16.

Is there a way that can I make sure that both sound devices always gets initialized correctly.
I tried with sudo sh –c “echo 1 > /sys/bus/rescan” as well as sudo alsa force-reload without success 
Could I add some configuration that always forces the initialization of the device.
Thanks in advance for any useful tips, hints or solutions.

Some extra info I gathered:

The sound related excerpt of sudo lspci –v
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
        Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family HD Audio Controller
       Flags: bus master, fast devsel, latency 0, IRQ 30
       Memory at f7c30000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
04:01.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
        Subsystem: ASUSTeK Computer Inc. Virtuoso 100 (Xonar ST)
Flags: bus master, medium devsel, latency 32, IRQ 11 <= IRQ 16 WHEN INITIALIZED CORRECTLY
        I/O ports at e000 [size=256]
        Capabilities: [c0] Power Management version 2
         Kernel driver in use: snd_virtuoso # <= ONLY WHEN INITIALIZED CORRECTLY
        Kernel modules: snd_virtuoso

The asound kernel version
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version k4.4.0-34-generic.

The asound version given by aplay –version is version 1.1.0

cat /proc/asound/modules when not initialized
 0 snd_hda_intel
 1 snd_hda_intel

cat /proc/asound/modules when initialized correctly
  0 snd_virtuoso
  1 snd_hda_intel
  2 snd_hda_intel

cat /proc/asound/cards when not initialized
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7c30000 irq 30
 1 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7c34000 irq 31

cat /proc/asound/cards when initialized correctly
 0 [STH6           ]: AV200 - Xonar ST+H6
                      Asus Virtuoso 100 at 0xe000, irq 16
 1 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf7c34000 irq 31
 2 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7c30000 irq 30

aplay –l when not initialized
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -l when initialized correctly
**** List of PLAYBACK Hardware Devices ****
card 0: STH6 [Xonar ST+H6], device 0: Multichannel [Multichannel]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: STH6 [Xonar ST+H6], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: PCH [HDA Intel PCH], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by percychris1 on 2016-08-16
The dmesg reported an error when trying to assign the index for the slot.  

```
[ 1.999752] snd_virtuoso 0000:04:01.0: cannot find the slot for index 0 (range 0-1), error: -16 
[ 1.999758] snd_virtuoso: probe of 0000:04:01.0 failed with error -16 –
```

So I decided to reorder the soundcards and moving the XONAR to the end with index 2.  

That worked fine but someone informed me that instead of using 

```
options snd_virtuoso index=2
options snd_hda_intel index=0
```

In ```
/etc/modprobe.d/alsa-base.conf
``` it is better to use

```
options snd slots=snd-hda-intel,snd-hda-intel,snd-virtuoso
```

---

