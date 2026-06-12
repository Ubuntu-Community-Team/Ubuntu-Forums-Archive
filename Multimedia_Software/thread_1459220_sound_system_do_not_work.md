---
title: "sound system do not work"
date: 2010-04-21
forum: Multimedia Software
---

### Post by bruncit on 2010-04-21
i'am just installed ubuntu. the problem now is my sound system is not work although it is not muted. its ok when using windows not in ubuntu. i've check the sound preference everything is not muted.
please help me..

---

### Post by economath on 2010-04-21
I am brand new to Linux and am having the same problem using Ubuntu 9.10 Karmic on a Dell Studio 17. Sound works fine on Windows 7 partition, but not at all on the Linux side. Plus it's not clear at all what sound card I have... Perhaps someone might be able to tell me what sound card I have from my output below when I type: sudo lshw -short

When I type:

sudo lshw -short

I get the following:

H/W path           Device      Class          Description
=========================================================
                               system         Studio 1749
/0                             bus            Motherboard
/0/1                           memory         124KiB BIOS
/0/3                           bus            0KVMW2
/0/5                           processor      Intel(R) Core(TM) i7 CPU       M 6
/0/5/6                         memory         64KiB L1 cache
/0/5/7                         memory         256KiB L2 cache
/0/5/8                         memory         4MiB L3 cache
/0/12                          memory         8GiB System Memory
/0/12/0                        memory         4GiB SODIMM Synchronous 1066 MHz (
/0/12/1                        memory         4GiB SODIMM Synchronous 1066 MHz (
/0/100                         bridge         Arrandale DRAM Controller
/0/100/1                       bridge         Arrandale PCI Express x16 Root Por
/0/100/1/0                     display        ATI Technologies Inc
/0/100/1/0.1                   multimedia     ATI Technologies Inc
/0/100/16                      communication  5 Series/3400 Series Chipset HECI 
/0/100/1a                      bus            5 Series/3400 Series Chipset USB2 
/0/100/1b                      multimedia     5 Series/3400 Series Chipset High 
/0/100/1c                      bridge         5 Series/3400 Series Chipset PCI E
/0/100/1c.1                    bridge         5 Series/3400 Series Chipset PCI E
/0/100/1c.1/0      eth2        network        BCM4312 802.11b/g
/0/100/1c.2                    bridge         5 Series/3400 Series Chipset PCI E
/0/100/1c.3                    bridge         5 Series/3400 Series Chipset PCI E
/0/100/1c.3/0                  bus            O2 Micro, Inc.
/0/100/1c.3/0.1                generic        O2 Micro, Inc.
/0/100/1c.3/0.2                storage        O2 Micro, Inc.
/0/100/1c.4                    bridge         5 Series/3400 Series Chipset PCI E
/0/100/1c.5                    bridge         5 Series/3400 Series Chipset PCI E
/0/100/1c.5/0      eth0        network        RTL8111/8168B PCI Express Gigabit 
/0/100/1d                      bus            5 Series/3400 Series Chipset USB2 
/0/100/1e                      bridge         82801 Mobile PCI Bridge
/0/100/1f                      bridge         Mobile 5 Series Chipset LPC Interf
/0/100/1f.2        scsi0       storage        5 Series/3400 Series Chipset 4 por
/0/100/1f.2/0      /dev/sda    disk           500GB TOSHIBA MK5056GS
/0/100/1f.2/0/1    /dev/sda1   volume         39MiB Windows FAT volume
/0/100/1f.2/0/2    /dev/sda2   volume         14GiB Windows NTFS volume
/0/100/1f.2/0/3    /dev/sda3   volume         117GiB Windows NTFS volume
/0/100/1f.2/0/4    /dev/sda4   volume         333GiB EXT4 volume
/0/100/1f.2/1      /dev/sdb    disk           500GB TOSHIBA MK5056GS
/0/100/1f.2/1/1    /dev/sdb1   volume         446GiB EXT4 volume
/0/100/1f.2/1/2    /dev/sdb2   volume         18GiB Extended partition
/0/100/1f.2/1/2/5  /dev/sdb5   volume         18GiB Linux swap / Solaris partiti
/0/100/1f.2/0.0.0  /dev/cdrom  disk           DVD+-RW GA31N
/0/100/1f.3                    bus            5 Series/3400 Series Chipset SMBus
/0/100/1f.6                    generic        5 Series/3400 Series Chipset Therm
/0/101                         bridge         QuickPath Architecture Generic Non
/0/102                         bridge         QuickPath Architecture System Addr
/0/103                         bridge         QPI Link 0
/0/104                         bridge         QPI Physical 0
/0/105                         bridge         Intel Corporation
/0/106                         bridge         Intel Corporation
/0/0               scsi6       storage        
/0/0/0.0.0         /dev/sdc    disk           320GB SCSI Disk
/0/0/0.0.0/1       /dev/sdc1   volume         298GiB Windows FAT volume
/1                             power          DELL N8
/2                             system         
/3                             power          To Be Defined By O.E.M

---

### Post by lidex on 2010-04-21
Both you guys ^^ go here first for generic sound issues in karmic:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Work through the page and post here any questions you may have as well as your results. Still no sound? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by economath on 2010-04-21
Thanks for the tips lidex!

I went to the debugging page. I seemed to have passed on all the diagnosis tests OK but still have no sound:


[LIST]
[*]my kernel version is not old (Karmic)
[/LIST]
```
uname -r
2.6.31-20-generic
```
[LIST]
[*]my sound driver doesn't appear to need to be updated
[/LIST]
```
dmesg | grep -i hda
[   14.857910] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.857962] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.982719] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   14.998480] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   14.998516] input: HDA Intel Line Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   14.998548] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   14.999212] HDA Intel 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   14.999248] HDA Intel 0000:02:00.1: setting latency timer to 64
[   18.982492] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
```
[LIST]
[*]no other process seems to be locking the sound card
[/LIST]
```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for michael: 
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  michael    1688 F.... pulseaudio
```
[LIST]
[*]I don't have the channel mapping problem associated with the ICE1712 chip
[/LIST]
```
michael@michael-laptop:~/www$ cat /proc/asound/cards | grep ICE1712
michael@michael-laptop:~/www$
```
[LIST]
[*]my sound card doesn't seem to need non-free firmware
[/LIST]
```
michael@michael-laptop:~/www$ dmesg | grep firmware
michael@michael-laptop:~/www$
```As for the commands you suggest I try, I have posted them along with their output in the code tags below.

```
uname -a
Linux michael-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
``````
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
``````
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.
``````
head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD73C1X5

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI
```My laptop is a Dell, the model is Studio 1749. I went to the Windows side under control panel --> system --> device manager --> sound, video and games: it said ATI High Definition Audio Device & IDT High Definition Audio CODEC. I'm not sure if that helps but I hope I've provided enough information.

---

### Post by Yellow Pasque on 2010-04-21
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
Copy/paste this line to the end of the file:
```
options snd-hda-intel model=*keyword*
```
Replace *keyword* with one of the following (e.g. dell-m6):

```
STAC92HD73*
===========
  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  intel		Intel DG45* mobos
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  alienware	Alienware M17x
  auto		BIOS setup (default)
```

When you're finished, save the file, quit, and reboot.

---

### Post by lidex on 2010-04-21
Actually you probably could stand an upgrade in alsa. Try installing the alsa-backports package from that troubleshooting page. Another option for alsa-base.conf:
```
options snd-hda-intel model=dell-bios

```
This just worked for another dell user. The dell-m6 option I would think also. But only use one at a time until it works. My laptop needed both an alsa upgrade and the widget options to work.

---

### Post by economath on 2010-04-21
Success! Thanks lidex and Temüjin! =D>

I tried Temüjin's idea and it worked for "dell-m6" and for "dell-m6-amic" after I discovered something silly: "System --> Preferences --> Sound --> Output [tab] --> Internal Audio Analog Stereo [click instead of "HD-Audio Generic Digital Stereo (HDMI)"]" So, once "Internal Audio Analog Stereo" was clicked and "dell-m6" was pasted in the "/etc/modprobe.d/alsa-base.conf" file, I got my sound working (after I had saved that file, closed it and rebooted).

Thanks lidex: I installed the alsa-backports package from the troubleshooting page after I had got my sound working. My sound still functions perfectly since I have installed that package.

---

### Post by bravo_s on 2010-05-03
Hi,

I also have Dell Studio 1749 and in Ubuntu 10.04 I had problem only with the sound from the headphones. Actually there was no sound. The problem was not solved with ALSA upgrade from version 1.0.20 to 1.0.23 (using following guide [http://monespaceperso.org/blog-en/2010/04/17/upgrade-alsa-1-0-23-on-ubuntu-karmic-koala-9-10/]("http://monespaceperso.org/blog-en/2010/04/17/upgrade-alsa-1-0-23-on-ubuntu-karmic-koala-9-10/")). I had to add
```
options snd-hda-intel model=dell-m6-amic
```
at the bottom of my /etc/modprobe.d/alsa-base.conf

Thought this could be useful if someone has problem only with the headphones ;)

Cheers!

---

### Post by arago on 2010-05-05
Hello all.
Googling around i found this thread.
I own a dell 1749 with i3.
I was looking for a working solution for headphone.
adding the line "options snd-hda-intel model=dell-m6-amic" i got the headphones working, but i loose microphone (integrated one) that works before.

I'm using a 10.04 - 64 bit ubuntu.

Thanks

---

### Post by lidex on 2010-05-05
> **arago said:**
> Hello all.
Googling around i found this thread.
I own a dell 1749 with i3.
I was looking for a working solution for headphone.
adding the line "options snd-hda-intel model=dell-m6-amic" i got the headphones working, but i loose microphone (integrated one) that works before.

I'm using a 10.04 - 64 bit ubuntu.

Thanks
Have you tried upgrading alsa? 
Also try different options (only one at a time):
```
options snd-hda-intel model=dell-m6-dmic
options snd-hda-intel model=dell-m6
options snd-hda-intel model=dell-eq
options snd-hda-intel model=auto
```
You need to reboot after making changes.

---

### Post by bravo_s on 2010-05-06
Hi arago,
You are right. My mic does not work either.

options snd-hda-intel model=dell-m6-dmic

should fix things. At least it worked for me.

---

### Post by gchadder3 on 2010-06-12
Thanks!

This exact solution solved my problem, too.  I also have a Dell Studio 1749.

---

### Post by happyemm25 on 2012-11-20
Found this thread today.  I updated to 12.04 on my Fujitsu Lifebook T4220 last week and today discovered the headphones no longer put the computer speakers on mute.

Wasn't sure if this thread would work, but I added options snd-hda-intel model=intel to the alsa-base.conf and restarted, and it worked perfectly.  I'm sure it's not the precise solution I should have used, but as a newbie (still so after 2.5 years in Ubuntu) I was thrilled this worked.

Thanks!!

---

