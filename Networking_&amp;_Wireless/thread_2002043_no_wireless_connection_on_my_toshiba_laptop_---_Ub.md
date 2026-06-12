---
title: "no wireless connection on my toshiba laptop --- Ubuntu 12.04"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by nzy102 on 2012-06-12
Hi Guys:

My wirelss connection has not been working for a while. I pretty much tried everything I saw from this board but still could not find a solution. I am wondering if anyone here can help me out a bit. 

When I type in lspci, here is what I got:

=========================================================================
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
========================================================================

when I typed in lsmod, here is what I got:

========================================================================
Module                  Size  Used by
joydev                 17393  0 
rfcomm                 38139  0 
parport_pc             32114  0 
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
binfmt_misc            17292  1 
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
psmouse                72919  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67203  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
videodev               86588  1 uvcvideo
i915                  414672  3 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
toshiba_acpi           18158  0 
sparse_keymap          13658  1 toshiba_acpi
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
wmi                    18744  1 toshiba_acpi
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 
=========================================================================

Thanks a lot in advance.

---

### Post by chili555 on 2012-06-12
We don't see anything that is wireless. Please run and post:```
lsusb
lspcmcia ident
rfkill list all
```Thanks.

---

### Post by nzy102 on 2012-06-12
Here it is:

===========================================================================

nzy102@lionHeart:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
nzy102@lionHeart:~$ lspcmcia ident
nzy102@lionHeart:~$ rfkill list all
nzy102@lionHeart:~$ 

========================================================================

---

### Post by chili555 on 2012-06-12
I still see nothing that is wireless. Is it enabled in the BIOS? Is there a switch that's off? Is it defective?

---

### Post by nzy102 on 2012-06-13
Yes, it was enabled in BIOS... Is my wireless card defective or for some reason it just turned off ...

---

### Post by nzy102 on 2012-06-13
Here is what I got for ifconfig:

=========================================================================

nzy102@lionHeart:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:33:fe:08:7a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:33ff:fefe:87a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9907210 (9.9 MB)  TX bytes:752013 (752.0 KB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31393 (31.3 KB)  TX bytes:31393 (31.3 KB)

nzy102@lionHeart:~$ 

==========================================================================

---

### Post by chili555 on 2012-06-13
I'm very sorry. We still see nothing that is a wireless device.

---

