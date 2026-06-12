---
title: "No Sound, ubuntu 8.04"
date: 2009-11-25
forum: Multimedia Software
---

### Post by DeimonDB on 2009-11-25
Hi,
I have installed ubuntu a few weeks ago, and since that there are no sound playing at all.

here are the output of some commands I saw at other posts :

aplay -l
> 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
lspci
> 
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:07.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:07.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:07.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)
06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
Can someone help me solve this ?

---

### Post by DeimonDB on 2009-11-26
hello?

---

### Post by babarosa on 2009-11-26
Hi,

22 hours is not very long to wait for an answer.

To play multimedia files (e.g. "sound") you have to install the proper codecs.

Follow these excellent guides 
[LIST]1.) Comprehensive Multimedia & Video Howto[/LIST]
[LIST]2.) Comprehensive Sound Problem Solutions Guide[/LIST]

You'll find both on top of this forum "Multimedia & Video" in the "Sticky Threads" Chapter.

Regards,
Michael

---

### Post by DeimonDB on 2009-11-26
Thanks for the reply,

I followed the Comprehensive Sound Problem Solutions Guide. But at step 3, I can't find my sound card, because the URL provided ([[SIZE=2]http://www.alsa-project.org/alsa-doc/[/SIZE]]("http://www.alsa-project.org/alsa-doc/")) does not show any matrix or dropdown box. It only show a list of file..

For the Comprehensive multimedia & video howto, I don't follow it, as I am sure the problem is not my codec, because I don't hear any sounds at all, including the login and logout sound, which should be able to be played without any codec or player.

---

### Post by ilil on 2009-11-26
Maybe sound is muted? Try to open gnome-volume-control and unmute all devices...

---

### Post by DeimonDB on 2009-11-26
nope, I have checked that multiple times..

---

### Post by ilil on 2009-11-26
Is it laptop? Maybe you mute sound with hardware button?

So, I think your problem is not ubuntu-centric, try googling for common problems with ALSA

---

### Post by DeimonDB on 2009-11-26
Yes, it is a laptop. but I'm sure it is not muted.
my laptop is dell studio xps 13.

I have done some searching before posting in this forum, but no solution works so far.

some I have tried :
- check whether sound is muted
- check soundcard with aplay -l and lspci command
- add options snd-hda-intel probe_mask=1 and options snd-hda-intel model=dell-m6 to alsa-base (although i'm not sure mine is hda intel)

btw, sound works fine in windows vista.

---

### Post by DeimonDB on 2009-11-26
I suspect my soundcard is not supported by ALSA yet. Can someone find it out for me? I don't quite understand to use the matrix at ALSA page..

---

### Post by ilil on 2009-11-26
Maybe [this](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483332)?
I think it is fairly new sound card so you need install more recent ubuntu version

P.S. Try googling [that]("http://www.google.com/search?q=Audio+device%3A+nVidia+Corporation+MCP79+High+Definition+Audio")

---

### Post by DeimonDB on 2009-11-26
hmm.. what is linux-backports-modules-alsa-karmic-generic? what is the version of this package in hardy?
Maybe I can play sound by changing model to mbp5..

---

### Post by ilil on 2009-11-26
I dont know. And yes, maybe backports for Hardy will help you

---

### Post by DeimonDB on 2009-11-27
Oh no, I installed linux backport, and rebooted. after that in the OS selection text, there are new options available, ubuntu kernel 2.xxxxx (a newer version). I select that option. Now the screen resolution is only 800 x 600 (which I have solved before by installing nvidia driver). aplay -l now output no soundcard found.. Any Suggestion?

---

