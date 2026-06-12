---
title: "No working sound on rear panel audio with headphones 16.04 LTS Ubuntu"
date: 2016-05-27
forum: Multimedia Software
---

### Post by john561 on 2016-05-27
I also have issues with headphones not being detected. Tried the method of commenting out a line in a file as mentioned in this thread, but didn't have any effect. I have a Realtek ALC1150 chip with HDA Intel PCH card. However connecting to front panel works as headphones built in audio appears in sound settings. Tried alsamixer, pavucontrol, etc...starting to think that 16.04  might have support problems with the audio chipset and card or something.

---

### Post by john561 on 2016-05-27
Greetings everyone,

I made a fresh install on a separate disk, so I have dual boot with Win 7. Now, while setting things up, I noticed that Ubuntu is not giving out any sound whatsoever as I tried testing it. I use my headphone most of the time and they are plugged with 1/8 jack on the rear panel. 

So I've been having issues with setting up sound lately and I have days  trying to figure out what it could be. Tried various "solutions" that found online (including in these forums) that  worked for some, but no luck on my end. I did however notice that if I plug them on the front panel, the "Headphones-Built in Audio" appears in Sound Settings under "Play Sound Through" and I can hear sound. So I feel like it's a rear panel issue and Ubuntu, since it work perfect in Windows 7 as I hear sound and use the microphone. 

Posted screenshots as I believe it's easier to understand what I am talking about. 

The only options I have in Sound Settings are the ones shown in Pic. 2. I did alsamixer and this is what I have, shown in Pic. 1. I did aplay -l to check on playback devices as shown in Pic. 3 to see if the soundcard wasn't being detected, but according to what I read, it is since it's ALC1150. 

I read that since Ubuntu 16.04 is relatively somewhat new, there may be still some things required to work out and fix, but I'm not sure how true that is. 

Thank you for your time and I hope there is a solution out there. 


[ATTACH=CONFIG]269318[/ATTACH]
[SIZE=3]**Pic. 1**[/SIZE]

[ATTACH=CONFIG]269319[/ATTACH]
[SIZE=3]**Pic. 2**[/SIZE]

[ATTACH=CONFIG]269320[/ATTACH]
[SIZE=3]**Pic. 3**[/SIZE]

---

### Post by DuckHook on 2016-05-27
*Two posts merged to one thread in **Multimedia Software**.* Please do not double post as it dilutes community effort.

Hi and welcome to the forums, john561.

Sound problems are notoriously difficult to diagnose.

Thank you for attaching sufficient info to help you with. With terminal output as in Picture 3, it is better to copy all of the output using your mouse and paste it to the thread  between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

You mention that you listen with headphones. However, the device you have selected is a digital output. Moreover, there is a BOSE device connected to Analog Output. Do you have another set of speakers connected via USB? If not, have you tried selecting that output?

Please post results of:```
lspci -vk | grep -iA8 audio
``````
lsusb
``````
sudo lshw -sanitize -C multimedia
```

---

### Post by john561 on 2016-05-30
Sorry about double post, I honestly have no idea how that came to be. I'm confused myself about it. 

Here are the results for each of the commands you suggested. 

```
lspci -vk | grep -iA8 audio
``` Results:

```
00:1b.0 Audio device: Intel Corporation 9 Series Chipset Family HD Audio Controller
    Subsystem: Micro-Star International Co., Ltd. [MSI] 9 Series Chipset Family HD Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f7210000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 9 Series Chipset Family PCI Express Root Port 1 (rev d0) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0, IRQ 16
--
01:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
    Subsystem: ASUSTeK Computer Inc. GM204 High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel

03:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 13)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Killer E220x Gigabit Ethernet Controller
```


```
lsusb
``` Results:

```
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bc2:3320 Seagate RSS LLC SRD00F2 [Expansion Desktop Drive]
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 05a7:1020 Bose Corp. 
Bus 003 Device 003: ID 046d:c24d Logitech, Inc. G710 Gaming Keyboard
Bus 003 Device 002: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 003 Device 005: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


```
sudo lshw -sanitize -C multimedia
```Results:

```
  *-multimedia            
       description: Audio device
       product: GM204 High Definition Audio Controller
       vendor: NVIDIA Corporation
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:17 memory:f7080000-f7083fff
  *-usb:2
       description: Audio device
       product: Bose USB Audio
       vendor: Bose Corporation
       physical id: 9
       bus info: usb@3:9
       version: 1.00
       capabilities: usb-1.00 audio-control
       configuration: driver=usbhid speed=12Mbit/s
  *-multimedia
       description: Audio device
       product: 9 Series Chipset Family HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:29 memory:f7210000-f7213fff

```


Also here's the result for ```
aplay -l
``` 

```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC1150 Analog [ALC1150 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1150 Digital [ALC1150 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Audio [Bose USB Audio], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```


Note: I am able to hear audio through the Bose USB Audio configuring in pavucontrol. Still having issues with headphones and rear panel audio. Yes, Ubuntu detected headphones when I connect them on the front panel of the PC. However the rear panel is the one giving me issues and it's the one I'm trying to connect to

---

### Post by DuckHook on 2016-06-01
Are your rear headphones connected through headphone jack or line out?

Do you use HDMI sound at all? If not, it sometimes helps to disable it in your BIOS. Card 0 seems to be the one you need to work on. Card 1 is HDMI and Card 2 is your USB BOSE speakers. For some reason, Card 0 is showing as digital output when it should be analogue. Does your MOBO have a S/PDIF connection? It's usually either a fibre optic connector or an odd-looking coaxial one.

---

### Post by john561 on 2016-06-01
Headphones connected thru headphone jack. 

No, I do not use HDMI sound. 

Yes my mobo has s/pdif ports.

---

### Post by DuckHook on 2016-06-01
1. Try unplugging USB Bose speakers and disabling HDMI in BIOS, if possible.Then reboot.

2. Also try setting output to analogue instead of digital in BIOS. Some MOBOs allow this.

3. Try plugging in headphones to line out instead of headphone jacks.

In each of the above scenarios, open alsa mixer to see if device appears.

---

### Post by Yellow Pasque on 2016-06-01
If ALSA is not recognizing your headphone jack as a headphone jack, you can use hdajackretask:

```
sudo apt-get install alsa-tools-gui
hdajackretask
```

More information could be helpful if you cannot figure out what pin is supposed to be your headphones: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by john561 on 2016-06-02
> **DuckHook said:**
> 1. Try unplugging USB Bose speakers and disabling HDMI in BIOS, if possible.Then reboot.

2. Also try setting output to analogue instead of digital in BIOS. Some MOBOs allow this.

3. Try plugging in headphones to line out instead of headphone jacks.

In each of the above scenarios, open alsa mixer to see if device appears.

So I tried method No.3. Switched to line out and it works! I can hear sound! Tested sound and works perfectly. I don't know how, I have to ask though, I could hear in my Win 7 while it was connected to the headphones jack in the rear panel. What difference is there between the two? Line Out and headphone?

---

### Post by DuckHook on 2016-06-03
As Temüjin points out, in order to output to any channel (headphones being one such channel), that channel must first be defined in the sound subsystem. The problem is that every audio card manufacturer designs their cards for Windows and provides a closed driver that is exhaustively tested for Windows. However, they couldn't give a rat's patooie about Linux and won't publish their specs or designs, so Linux open-source drivers must be reverse engineered to work with the card. Since there are more cards out there than leaves on a tree, and a limited number of Linux driver developers, it is not surprising that many audio cards aren't completely channel-mapped. This seems to be the case in your situation. Line out has been properly mapped, but rear headphones has not.

You can define the channel map yourself and modify a configuration file to open the right channel to rear headphones. Temüjin has kindly provided you with a link to beginning such a process. However, it is obscure, arcane and the stuff of command line nightmares that new users usually find discouraging about Linux. Not the fault of Linux, because the manufacturers won't release development specs, but the result is still limited utility.

I recommend that you just use line out instead of wrestling with that alligator, unless, of course, you want to educate yourself.

---

### Post by john561 on 2016-06-03
> **DuckHook said:**
> As Temüjin points out, in order to output to any channel (headphones being one such channel), that channel must first be defined in the sound subsystem. The problem is that every audio card manufacturer designs their cards for Windows and provides a closed driver that is exhaustively tested for Windows. However, they couldn't give a rat's patooie about Linux and won't publish their specs or designs, so Linux open-source drivers must be reverse engineered to work with the card. Since there are more cards out there than leaves on a tree, and a limited number of Linux driver developers, it is not surprising that many audio cards aren't completely channel-mapped. This seems to be the case in your situation. Line out has been properly mapped, but rear headphones has not.

You can define the channel map yourself and modify a configuration file to open the right channel to rear headphones. Temüjin has kindly provided you with a link to beginning such a process. However, it is obscure, arcane and the stuff of command line nightmares that new users usually find discouraging about Linux. Not the fault of Linux, because the manufacturers won't release development specs, but the result is still limited utility.

I recommend that you just use line out instead of wrestling with that alligator, unless, of course, you want to educate yourself.

Ahh, I see. So it's a problem due to lack of support more than anything else. I'll stick with Line Out for now. I bookmarked Temujin's link to try and do the mapping once I feel comfortable managing Linux. Thanks for the help.

---

### Post by john561 on 2016-06-03
> **Temüjin said:**
> If ALSA is not recognizing your headphone jack as a headphone jack, you can use hdajackretask:

```
sudo apt-get install alsa-tools-gui
hdajackretask
```

More information could be helpful if you cannot figure out what pin is supposed to be your headphones: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

Thank you for your reply and help. I was able to solve the issue by changing to Line Out. I will however bookmark that link to read up more

---

### Post by DuckHook on 2016-06-03
*Please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

