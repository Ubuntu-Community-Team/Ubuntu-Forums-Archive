---
title: "Sound Problems on Sony NR-21Z-T on 9.04"
date: 2009-10-28
forum: Multimedia Software
---

### Post by hughw on 2009-10-28
On my sony NR21Z-T I have no sound at all. It used to be that the sound worked fine, but now, all I get when I try to play a sound is static.
[http://kmuto.jp/debian/hcl/Sony/VGN-NR21Z](http://kmuto.jp/debian/hcl/Sony/VGN-NR21Z) gives hardware info about the laptop.

any help would be much apreciated.

hughw

---

### Post by Ulysses361 on 2009-10-29
Please execute step 1, reboot and then send us output from step 3 and step 4 using this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by hughw on 2009-10-29
Step 3 output is at [http://pastebin.ca/1647740](http://pastebin.ca/1647740)

step 4 output is:
```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc300000 irq 22
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  asoundconf-gtk flashplugin-nonfree-extrasound gnome-alsamixer 
  libgconfmm-2.6-1c2{a} libglademm-2.4-1c2a{a} libpulse-mainloop-glib0{a} 
  padevchooser{a} paman{a} paprefs{a} pavucontrol{a} pavumeter{a} 
  pulseaudio-module-zeroconf{a} 
0 packages upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives. After unpacking 2781kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://gb.archive.ubuntu.com jaunty/universe asoundconf-gtk 1.6-0ubuntu1 [6444B]
Get:2 http://gb.archive.ubuntu.com jaunty/multiverse flashplugin-nonfree-extrasound 0.0.svn2431-3 [8160B]
Get:3 http://gb.archive.ubuntu.com jaunty/universe gnome-alsamixer 0.9.7~cvs.20060916.ds.1-2 [53.7kB]
Get:4 http://gb.archive.ubuntu.com jaunty/main libgconfmm-2.6-1c2 2.24.0-0ubuntu1 [31.1kB]
Get:5 http://gb.archive.ubuntu.com jaunty/main libglademm-2.4-1c2a 2.6.7-1 [21.4kB]
Get:6 http://gb.archive.ubuntu.com jaunty-updates/main libpulse-mainloop-glib0 1:0.9.14-0ubuntu20.2 [30.9kB]
Get:7 http://gb.archive.ubuntu.com jaunty/universe pavumeter 0.9.3-1ubuntu1 [29.2kB]
Get:8 http://gb.archive.ubuntu.com jaunty/universe pavucontrol 0.9.7-1ubuntu3 [66.0kB]
Get:9 http://gb.archive.ubuntu.com jaunty/universe paman 0.9.4-1ubuntu2 [92.2kB]
Get:10 http://gb.archive.ubuntu.com jaunty-updates/main pulseaudio-module-zeroconf 1:0.9.14-0ubuntu20.2 [18.4kB]
Get:11 http://gb.archive.ubuntu.com jaunty/universe paprefs 0.9.7-0ubuntu1 [35.2kB]
Get:12 http://gb.archive.ubuntu.com jaunty/universe padevchooser 0.9.3-2ubuntu4 [20.2kB]
Fetched 413kB in 0s (705kB/s)      
Selecting previously deselected package asoundconf-gtk.
(Reading database ... 220210 files and directories currently installed.)
Unpacking asoundconf-gtk (from .../asoundconf-gtk_1.6-0ubuntu1_all.deb) ...
Selecting previously deselected package flashplugin-nonfree-extrasound.
Unpacking flashplugin-nonfree-extrasound (from .../flashplugin-nonfree-extrasound_0.0.svn2431-3_i386.deb) ...
Selecting previously deselected package gnome-alsamixer.
Unpacking gnome-alsamixer (from .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_i386.deb) ...
Selecting previously deselected package libgconfmm-2.6-1c2.
Unpacking libgconfmm-2.6-1c2 (from .../libgconfmm-2.6-1c2_2.24.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-1_i386.deb) ...
Selecting previously deselected package libpulse-mainloop-glib0.
Unpacking libpulse-mainloop-glib0 (from .../libpulse-mainloop-glib0_1%3a0.9.14-0ubuntu20.2_i386.deb) ...
Selecting previously deselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.9.7-1ubuntu3_i386.deb) ...
Selecting previously deselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package pulseaudio-module-zeroconf.
Unpacking pulseaudio-module-zeroconf (from .../pulseaudio-module-zeroconf_1%3a0.9.14-0ubuntu20.2_i386.deb) ...
Selecting previously deselected package paprefs.
Unpacking paprefs (from .../paprefs_0.9.7-0ubuntu1_i386.deb) ...
Selecting previously deselected package padevchooser.
Unpacking padevchooser (from .../padevchooser_0.9.3-2ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up asoundconf-gtk (1.6-0ubuntu1) ...
Setting up flashplugin-nonfree-extrasound (0.0.svn2431-3) ...
Setting up gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2) ...

Setting up libgconfmm-2.6-1c2 (2.24.0-0ubuntu1) ...

Setting up libglademm-2.4-1c2a (2.6.7-1) ...

Setting up libpulse-mainloop-glib0 (1:0.9.14-0ubuntu20.2) ...

Setting up pavumeter (0.9.3-1ubuntu1) ...

Setting up pavucontrol (0.9.7-1ubuntu3) ...

Setting up paman (0.9.4-1ubuntu2) ...

Setting up pulseaudio-module-zeroconf (1:0.9.14-0ubuntu20.2) ...
Setting up paprefs (0.9.7-0ubuntu1) ...

Setting up padevchooser (0.9.3-2ubuntu4) ...

Processing triggers for menu ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done

Names of available sound cards:
Intel
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
total 0
crw-rw----+  1 root audio 116, 33 2009-10-29 12:39 timer
crw-rw----+  1 root audio 116,  1 2009-10-29 12:39 seq
crw-rw----+  1 root audio 116,  5 2009-10-29 12:39 hwC0D1
crw-rw----+  1 root audio 116,  4 2009-10-29 12:39 hwC0D0
crw-rw----+  1 root audio 116,  0 2009-10-29 12:39 controlC0
drwxr-xr-x   2 root root      180 2009-10-29 12:39 .
crw-rw----+  1 root audio 116, 24 2009-10-29 12:39 pcmC0D0c
crw-rw----+  1 root audio 116, 16 2009-10-29 12:39 pcmC0D0p
drwxr-xr-x  16 root root     4320 2009-10-29 12:47 ..
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)
Kernel: Linux hugh-laptop 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xfc300000 irq 22

Audio devices:
0: ALC262 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC262
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation G86M [GeForce 8400M GT] [10de:0426] (rev a1)
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 15)
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
08:03.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
08:03.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
08:03.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
/usr/sbin/alsactl
snd_hda_codec_realtek   208260  1 
snd_hda_intel          35712  3 
snd_hda_codec          87168  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                83716  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            36224  0 
snd_seq_midi           14496  0 
snd_rawmidi            29984  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    67236  20 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm

```

however, after step 1, the sound appears to work

---

