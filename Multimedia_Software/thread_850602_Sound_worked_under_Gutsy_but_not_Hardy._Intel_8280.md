---
title: "Sound worked under Gutsy but not Hardy. Intel 82801I ICH9 Family"
date: 2008-07-05
forum: Multimedia Software
---

### Post by BReflection on 2008-07-05
My sound worked under Gutsy, but now that I've upgraded to Hardy it doesn't work in either KDE 3 or KDE 4. I've tried all of the available sound servers, including ALSA, OSS, TOSS and ESD. My speakers are correctly plugged in to the analog port of my sound card. I've followed the [Comprehensive Sound Problems Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449) in addition to reading the [HDAIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). The only thing I haven't done is compile new alsa kernel modules. This is unnecessary since my sound worked under Gutsy. Unless the sound drivers have been downgraded between Gutsy/Hardy, then the ones on my system support my hardware. Although support for the Intel ICH9 Family is not listed on the ALSA wiki's [Intel matrix](https://help.ubuntu.com/community/HdaIntelSoundHowto), they do mention adding support for it in their [changelogs](http://www.alsa-project.org/main/index.php/Special:Search?search=ICH9&go=Go). In [this #Ubuntu IRC log](http://irclogs.ubuntu.com/2008/05/12/%23kubuntu.html), **egork** says they had the same symptoms as me and had to reinstall ubuntu-desktop to get it to work. I think what actually happened is that a byproduct of reinstalling ubuntu-desktop was to reinstall all of the alsa/sound packages, which I have done. In [this IRC log](http://irclogs.ubuntu.com/2008/06/19/%23kubuntu.txt), **Datalanche** had the same problem with the same hardware, and didn't receive much of an answer, other than to recompile his kernel modules. 

Here is the info about my setup:

[quote=lspci -v]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
        Subsystem: Giga-byte Technology Unknown device a022
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fa200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
[/quote]

[quote=sudo /sbin/modprobe -l | grep snd | grep intel]
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-intel8x0.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/snd-intel8x0m.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko

[/quote]

[quote=uname -a]Linux mist 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux[/quote]

[quote=lsb_release -a]No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy[/quote]

I suppose I will compile new kernel modules with the latest ALSA sources, but I strongly suspect it won't work:frown:

---

### Post by BReflection on 2008-07-05
I followed all of the instructions in the wiki article for HdaIntel cards, compiling the alsa driver, library and utilties from source and putting *options snd-hda-intel model=ALC885 probe_mask=1* in */etc/modprobe.d/alsa-base* to no avail.

---

### Post by BReflection on 2008-07-05
I fixed it!

By installing a new old sound card.

I installed the *Creative Labs SB Live! EMU10k1 (rev 07)*, rebooted and it worked with zero configuration.

---

### Post by Kydwn on 2008-07-07
> **BReflection said:**
> I fixed it!

By installing a new old sound card.

I installed the *Creative Labs SB Live! EMU10k1 (rev 07)*, rebooted and it worked with zero configuration.

You didnt fix it... You installed an old card...

:(

I have the same problem...

---

### Post by romansky on 2008-07-07
> **BReflection said:**
> My sound worked under Gutsy, but now that I've upgraded to Hardy it doesn't work

I have the same problem. From what I can gather, it seems it's due to a bug in the new kernel. I've seen several proposed work-arounds, some of wich you mention. They seem to work for some, but far from evertyone (e.g. me :-( ) I was really disappointed that this hadn't been taken care of in the 8.04.1 release, though. To me, it's a show stopping bug, as I've wiped Hardy and reverted to gutsy...

---

### Post by Datalanche on 2008-07-08
Hey. I see you mentioned I was having the same issue as you. Just for the record, I was able to fix my problem by following the HdaIntelSoundHowto guide. Compiling the latest ALSA driver, lib, and utils tarballs got my sound working on my Gigabyte GA-EP35-DS3L motherboard.  I can't really provide much else detail wise, as I've moved away from Linux for now(retrying soon but very frustrated), but the guide was all there was to it for me. Looks like this problem is very inconsistent, though. I hope it gets patched sometime! :(

---

### Post by ashgromnies on 2008-07-29
I recompiled all the latest ALSA drivers from their site, as well as the versions from Realtek and neither worked for me :(

---

### Post by jameslaw on 2008-07-30
None of the above suggestions worked for me. Last night I found the fix for my Dell laptop. See:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

---

### Post by stego_s_aurus on 2008-11-28
Tons and tons and tons of searching later, I ran across the solution!

We have an ASUS M50VM that has an Intel Corporation 82801I (ICH9 Family) HD Audio Controller (Rev 03). Couldnt get it to work, went through the entire OpenSound reconfiguration, Did the irqpoll thing, And the snd-hda-intel enable_msi = 1. No Dice.

Just before I went to sleep last night, I found some Other settings by searching for "options snd-hda-intel"... and Someone else had some additional settings that I added to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1

Did the edit, rebooted, and sure enough the lovely sound of drums!!!

Heres hoping this can help others from having to spend 8 hours looking for the info!!

-Stego

:KS:KS:KS

---

### Post by fdemmer on 2008-12-28
unfortunately the suggestions and hours of googling did not help me...

not irqpoll
not pci=noacpi
not model=... all in the ALSA-Configuration.txt
not probe_mask=1...2...4...8
not enable_msi=1
not single_cmd=1
not alsa-driver-1.0.18a from source
not vanilla 2.6.27 kernel

it DID work with gutsy, not sure if it broke  immediately with the hardy upgrade or a little later... but intrepid does not fix it.

i have an intel DG33TL with:
Intel 82801IR (ICH9R)
IDT STAC9271D audio codec

---

### Post by godvirus on 2009-04-04
I had this problem on my gigabyte ds3l desktop as well as my Dell Vostro 1500 laptop. The solution was simple:

1) sudo apt-get install alsamixergui

2) Run `alsamixergui`
   Click each "front" speaker icon, left and right. to enable. Then jack the PCM levels to max.

---

