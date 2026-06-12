---
title: "Ubuntu doesn't recognise sound card, video card after moving computer"
date: 2009-07-26
forum: Multimedia Software
---

### Post by deafpanda on 2009-07-26
Hello there,

Recently, I moved my ubuntu 8.04 machine from one room to another, after unsuccessfully trying to play a DVD on it.  Now ubuntu can't find my video or sound card - it starts in low graphics mode and won't play audio files.

Have I nudged my computer's innards out of shape, or is there another explanation?

I am new to all this, as you can tell.

Thanks a lot

---

### Post by igorzwx on 2009-07-26
Do not worry!
No miracles here.
The laws of physics are still valid.
Everything O.K.

The most probable explanation:
A day ago we discussed here some security problems,
Ubuntu botnets, remote exploits, etc.
It was a security update, perhaps.

---

### Post by martinbaselier on 2009-07-26
It's quite probable some cards are a bit loose. 
just to be sure:
Can you post the output of lspci ? 

open a terminal and type 

lspci > hardwareinfo.txt
gedit hardwareinfo.txt

Then paste the content of the file on the forum here.

---

### Post by deafpanda on 2009-07-26
Thanks.

> 00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Gigabit Ethernet Adapter
00:05.0 IDE interface: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01)
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:09.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

That's what I got!

Edit: my sound card is an m-audio delta audiophile 2496.

---

### Post by martinbaselier on 2009-07-26
> 00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)

That's your onboard soundcard. Definitely not m-audio. 

> 00:09.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)

I don't think that's your m-audio either. It seems the m-audio card is missing, but I could be wrong. 
**sudo lspci -v -s 00:09.0**
can give you more info. 

> 
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) 

Your video card is still there. It would be of course, otherwise you could not see anything. Do you use the open source driver or the one from Nvidea ?

---

### Post by deafpanda on 2009-07-26
Thanks again.

This is the output:
> 00:09.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
	Subsystem: VIA Technologies Inc. M-Audio Delta Audiophile
	Flags: medium devsel, IRQ 255
	I/O ports at a400 [disabled] [size=32]
	I/O ports at a000 [disabled] [size=16]
	I/O ports at 9800 [disabled] [size=16]
	I/O ports at 9400 [disabled] [size=64]
	Capabilities: [80] Power Management version 1

I use the open source drivers, I think.

I only have one sound card - the M-audio one (which, by the way, is manufactured by VIA technologies, a google search tells me).  It seems that ubuntu thinks I have a different sound card to the one that I actually have?

I think I may have installed some updates before the cards stopped being recognised.  Might this have affected things?

Thanks again for your help.

---

### Post by martinbaselier on 2009-07-26
You probable have an AC97 on your motherboard (which is quite normal) and an extra pci card. Everything is recognized correctly, but it doesn't load a driver. 

This link will show you how to install oss, an alternative to alsa. 
[http://ubuntuforums.org/showthread.php?t=1217259](http://ubuntuforums.org/showthread.php?t=1217259)

That should solve the sound problem.

I'll look into the video problem.

---

### Post by martinbaselier on 2009-07-26
What do you see in the restricted driver manager?

---

### Post by deafpanda on 2009-07-26
Thank you, I will try to follow those instructions.  In sound preferences, i have the option to use oss, alsa, "SiS SI7012" or pulseaudio.  Clicking "test" on any of these produces no sound.  Clicking "test" on alsa gives me the error:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

---

### Post by igorzwx on 2009-07-26
Martin!

On Ubuntu 8.04. it is not easy to install OSS4 for a beginner.
1. You should blacklist ALSA modules by hand
2. You should compile OSS4 from the Mercurial.

I made this already.
It is not an option for him.

He may try to install OSS4 on Ubuntu 9.04.
But he has 8.04

---

### Post by igorzwx on 2009-07-26
There is a nice book
Ubuntu Linux for Dummies.chm

read some 20 pages of this book
install another Ubuntu (9.04) in a dual boot (or multiple boot)
and make experiments there.

---

### Post by deafpanda on 2009-07-26
Installed latest updates and rebooted and I'm not in low graphics mode now (so I assume video card is working OK).  Still no sound.

---

### Post by igorzwx on 2009-07-26
Security problem is with PulseAudio.
8.04 is a business class.
Security is more important than anything else.

---

### Post by martinbaselier on 2009-07-26
Does your sound work after: 
sudo modprobe snd-ice1712

Just to be sure, I'd like to know what 

sudo lspci -v -s 00:09.0

shows after doing so.

---

### Post by Yellow Pasque on 2009-07-26
Check your BIOS/CMOS settings. Perhaps you have a dead mobo battery and unplugging the system caused the settings to reset to default.

While you're in the BIOS, just disable the onboard audio if there's an option for that (assuming you're not using it). That would be the easiest way to avoid sound device conflicts. IIRC, you can also use the *padevchooser* command and/or do something like this: [https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems#Configuring%20default%20soundcards%20/%20stopping%20soundcards%20from%20switching](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems#Configuring%20default%20soundcards%20/%20stopping%20soundcards%20from%20switching) (note that the command to edit your configuration file in Ubuntu 9.04 should be: *gksudo gedit /etc/modprobe.d/alsa-base.conf*

---

### Post by igorzwx on 2009-07-27
**[Root exploit for *Linux kernel* published - News - The H Security [B]...**]("http://www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791")[/B]

17 Jul 2009 **...** *Brad Spengler*, the developer behind the Grsecurity project, has published an exploit for a *vulnerability* in the Tun interface in *Linux kernel* 2.6.30 **...** The exploit uses loadable modules from *PulseAudio* which are set as **...**
[www.h-online.com/security/Root](www.h-online.com/security/Root)...**Linux**-**kernel**.../113791 - [Cached]("http://209.85.135.132/search?q=cache:_Xm8cw6--XkJ:www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791+vulnerability+linux+kernel+PulseAudio+Brad+Spengler&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.h-online.com/security/Root-exploit-for-Linux-kernel-published--/news/113791")

---

### Post by Yellow Pasque on 2009-07-27
igor, that doesn't apply to Ubuntu Hardy, which uses kernel 2.6.24, so I don't think any kernel updates would be installed due to that.

---

### Post by igorzwx on 2009-07-27
Security problems are never made transparent.
You know those security experts, KGB mentality.
A rumor, a publication in The Register is enough
to apply extreme measures.

---

