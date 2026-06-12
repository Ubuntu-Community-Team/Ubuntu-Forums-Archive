---
title: "Msi Leptop , no sound"
date: 2009-05-17
forum: Multimedia Software
---

### Post by 2chi on 2009-05-17
Hey.

 I recently install the latest ver. of Ubuntu 9.04 x64. on my [MSi]("http://www.msi.com/index.php?func=prodtmpspec&maincat_no=135&cat2_no=269&cat3_no=&prod_no=1677#menu") Laptop.
 Being new to Linux I'm pretty much lost in here.

 for now my main issue is that i can't get any sound. 
 i've tried just about anything i could find over the net. no luck yet.
 would really appreciate any help.

 1 - Checked for any muted channels, none.
 2 -  Installed Gnome Alsa Mixer. no problems there.m 
 3 - Checked under Sound pref and tried everything, none of them worked. For now i set
 all of them to alsa advanced Linux  sound architecture.
 4- Inside Volume Control - Set it to Hda Intel Alsa Mixer.
 5 - Tried those , No luck
pkill pulseaudio; sleep 2; pulseaudio -vv
alsamixer -Dhw


6 - Followed this [link]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html"), but didn't get any results. 
7 - Tried this [one]("http://ubuntuforums.org/showthread.php?t=919078") , still nothing
8 - And [This]("https://answers.launchpad.net/ubuntu/+question/69060") ....

*****************************************************************************************************************************
1:  cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8ef8000 irq 22

2: asoundconf list
Names of available sound cards:
Intel

3: sudo aptitude install hwinfo gnome-alsamixer asoundconf-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

4: hwinfo --sound
21: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_8086_293e
  Unique ID: u1Nb.u_BNWJ+LvyF
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Intel 82801I (ICH9 Family) HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x293e "82801I (ICH9 Family) HD Audio Controller"
  SubVendor: pci 0x1462 "Micro-Star International Co., Ltd."
  SubDevice: pci 0x6740 
  Revision: 0x03
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xf8ef8000-0xf8efbfff (rw,non-prefetchable)
  IRQ: 22 (8788 events)
  Module Alias: "pci:v00008086d0000293Esv00001462sd00006740bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

5:aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

6: cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.18rc3 emulation code)
Kernel: Linux bar-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xf8ef8000 irq 22

Audio devices:
0: ALC1200 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Realtek ALC1200

7: lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
05:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]
06:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 9500M GS [10de:0405] (rev a1)


8:lsmod | grep snd
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

9: grep audio /etc/group
audio:x:29:pulse

***************************************************************************************************************************

  
I'm stubborn as an ***, and really need some help here.
TNX. 
Dan.

 Ps: sorry for my English.   :oops:

---

### Post by 2chi on 2009-05-18
Bump

---

