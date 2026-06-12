---
title: "PeppermintOS wifi speed on Ubuntu"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by Alan|Cvette on 2010-11-20
Hi folks! Quick question, and if I'm in the wrong category feel free to move me!

Recently I downloaded and tested PeppermintOS and was amazed by the speed of the wifi compared to that of my Ubuntu 10.10 which is a nightmare. How if at all can I incorporate the PeppermintOS wifi in my Ubuntu?

---

### Post by puppywhacker on 2010-11-20
never heard of peppermint, but it's a linux anyway. incorporating is not an option, customizing is.

In linux you can use the propitiatory drivers from the vendor, the opensource clones or the windows ndis wrapper drivers. Personally I only would use the opensource drivers. If you rightclick the upanddown arrow in the right top of the screen and choose "connection information" it would show the name of the driver you are using. For Ubuntu you are probably using the wrong default one.

now, without specific details about your card its difficult to say anything that will actually help you, so if you can post some details. Try to find the wireless related information from any of these commands.

```
sudo lsmod
sudo lspci
sudo dmesg

```

---

### Post by Alan|Cvette on 2010-11-20
Hi! Thanks for the reply. To start off, I have a Netopia USB card model # TER/GUSB2-N that was given to us by AT&T a few years ago, it uses Ralink RT73 drivers.

Here is the output from Ubuntu.

```
alan@alan-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c062 Logitech, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f2:0841 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 148f:9021 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 002 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```
alan@alan-desktop:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc             7984  1 
vboxnetadp              5267  0 
vboxnetflt             14966  0 
vboxdrv              1792984  2 vboxnetadp,vboxnetflt
parport_pc             30086  0 
ppdev                   6804  0 
i915                  330249  4 
drm_kms_helper         32836  1 i915
drm                   206161  5 i915,drm_kms_helper
arc4                    1497  2 
snd_hda_codec_realtek   299533  1 
psmouse                62080  0 
rt73usb                24308  0 
rt2x00usb              11316  1 rt73usb
rt2x00lib              31575  2 rt73usb,rt2x00usb
i2c_algo_bit            6208  1 i915
lp                     10201  0 
video                  22176  1 i915
intel_agp              32080  2 i915
serio_raw               4910  0 
led_class               3393  1 rt2x00lib
snd_hda_intel          26019  4 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
output                  2527  1 video
snd_pcsp                9507  1 
snd_hwdep               6660  1 snd_hda_codec
snd_seq_midi            5932  0 
parport                37032  3 parport_pc,ppdev,lp
snd_pcm                89104  4 snd_hda_intel,snd_hda_codec,snd_pcsp
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
mac80211              266657  2 rt2x00usb,rt2x00lib
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
evbug                   2269  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_i801               10156  0 
snd                    64117  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcsp,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
cfg80211              170293  2 rt2x00lib,mac80211
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
usbhid                 42062  0 
hid                    84678  1 usbhid
usb_storage            50372  0 
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  2 rt73usb,firewire_core
r8169                  42222  0 
ahci                   21857  0 
libahci                26167  3 ahci
mii                     5261  1 r8169
```

```
alan@alan-desktop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

```

```
[  682.019535] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.019550] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.027535] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -3
[  682.027550] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.035537] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.035552] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.043538] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  682.043553] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.123545] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.123552] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  682.123567] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.131546] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.131553] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  682.131567] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.139546] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 3
[  682.139553] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 7
[  682.139567] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.155548] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  682.155556] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  682.155570] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.163549] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  682.163557] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 7
[  682.163571] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.171551] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  682.171566] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.179549] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.179557] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  682.179571] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.187555] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  682.187569] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.195552] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  682.195566] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.203552] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.203559] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  682.203572] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.211553] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  682.211568] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.219556] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  682.219571] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.227554] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.227562] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 5
[  682.227575] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.235557] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.235564] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  682.235578] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.243559] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  682.243573] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.251558] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.251566] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 5
[  682.251580] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.259557] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  682.259564] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  682.259579] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.267560] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.267568] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  682.267581] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.275562] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  682.275577] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.283562] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  682.283577] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.291300] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  682.291314] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.339566] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.339574] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.339588] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.347569] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -3
[  682.347576] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  682.347590] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.355569] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  682.355577] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -5
[  682.355591] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.363570] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -3
[  682.363577] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -6
[  682.363592] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.371571] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -3
[  682.371578] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -7
[  682.371593] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.379571] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  682.379578] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -7
[  682.379592] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.387573] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  682.387580] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  682.387594] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.395573] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -6
[  682.395581] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -15
[  682.395595] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.403582] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  682.403590] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  682.403605] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.411582] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -5
[  682.411590] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  682.411605] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.419578] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -6
[  682.419585] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  682.419600] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.427577] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -7
[  682.427585] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  682.427599] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.435578] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -7
[  682.435586] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  682.435600] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.443578] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -7
[  682.443586] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -8
[  682.443600] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.451583] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -6
[  682.451590] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -7
[  682.451605] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.459580] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -5
[  682.459588] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -6
[  682.459602] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.467567] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -3
[  682.467576] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -4
[  682.467592] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.475592] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  682.475600] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  682.475617] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.483588] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.483604] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.491586] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  682.491594] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.491609] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.499591] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.499599] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  682.499616] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.507589] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  682.507597] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.507611] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.515586] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  682.515593] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -3
[  682.515607] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.523588] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -5
[  682.523595] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -5
[  682.523610] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.539587] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  682.539595] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.539608] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.547589] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -3
[  682.547596] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -4
[  682.547610] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.555588] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.555596] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.555609] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.563590] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  682.563598] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  682.563612] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.571593] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.571601] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.571615] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.579592] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.579599] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  682.579614] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.587596] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.587604] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  682.587618] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.595595] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.595603] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.595617] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.603595] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.603602] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  682.603617] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.611596] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.611603] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.611617] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.619595] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.619603] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -3
[  682.619617] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.627600] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.627615] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.635599] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.635607] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -3
[  682.635621] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.643602] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  682.643609] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -3
[  682.643625] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.651602] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  682.651617] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.659607] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  682.659623] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.723610] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  682.723617] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  682.723631] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.731609] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 3
[  682.731617] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  682.731631] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.739609] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  682.739617] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  682.739631] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.747613] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 3
[  682.747621] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  682.747635] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.755613] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 4
[  682.755620] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 5
[  682.755635] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.763612] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 5
[  682.763619] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 6
[  682.763633] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.771614] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 11
[  682.771622] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 14
[  682.771636] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.779613] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 7
[  682.779621] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 9
[  682.779635] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.787619] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 6
[  682.787626] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 10
[  682.787641] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.795610] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 7
[  682.795615] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 9
[  682.795625] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.803625] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 6
[  682.803633] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 10
[  682.803648] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.811620] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 6
[  682.811627] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 9
[  682.811642] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.819618] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 5
[  682.819625] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 10
[  682.819640] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.827619] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 6
[  682.827626] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 9
[  682.827640] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.835631] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 4
[  682.835639] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 8
[  682.835656] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.843629] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 5
[  682.843637] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 8
[  682.843653] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.851623] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 3
[  682.851630] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 7
[  682.851644] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.859622] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 3
[  682.859630] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 5
[  682.859644] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.867622] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  682.867630] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  682.867643] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.875623] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.875630] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  682.875644] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.883625] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.883633] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  682.883648] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.891624] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  682.891631] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  682.891645] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.899625] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  682.899632] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  682.899646] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.907627] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  682.907635] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  682.907649] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.915626] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 3
[  682.915633] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  682.915646] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.923629] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  682.923636] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  682.923650] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.939632] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  682.939647] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  682.995638] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  682.995652] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.003636] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.003643] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.003658] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.011640] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.011655] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.019636] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.019642] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.019655] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.027641] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.027656] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.035641] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.035648] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.035662] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.043642] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  683.043657] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.051643] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.051650] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.051664] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.059642] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.059650] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  683.059663] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.067644] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.067651] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  683.067665] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.075645] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.075652] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  683.075666] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.083643] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 5
[  683.083650] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 7
[  683.083665] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.091653] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 3
[  683.091661] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 5
[  683.091675] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.099646] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  683.099654] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 4
[  683.099671] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.107637] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  683.107646] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 3
[  683.107662] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.115660] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 2
[  683.115668] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  683.115686] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.123647] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.123654] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  683.123667] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.131647] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.131654] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.131667] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.139657] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.139674] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.147651] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.147658] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.147672] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.155652] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.155667] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.163652] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.163659] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  683.163672] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.171652] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.171658] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.171672] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.179652] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.179666] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.187652] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.187658] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.187671] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.195654] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.195661] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.195674] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.203656] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  683.203670] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.211653] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  683.211668] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.275649] evbug.c: Event. Dev: input4, Type: 4, Code: 4, Value: 589825
[  683.275655] evbug.c: Event. Dev: input4, Type: 1, Code: 272, Value: 1
[  683.275681] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.331665] evbug.c: Event. Dev: input4, Type: 4, Code: 4, Value: 589825
[  683.331672] evbug.c: Event. Dev: input4, Type: 1, Code: 272, Value: 0
[  683.331700] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.435691] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  683.435710] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.483688] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  683.483696] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  683.483710] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.491684] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  683.491691] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  683.491704] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.499687] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  683.499702] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.579706] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  683.579726] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.587698] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  683.587706] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  683.587719] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.595695] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  683.595702] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  683.595715] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.603698] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  683.603706] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  683.603720] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.611698] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  683.611705] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  683.611718] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.619698] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  683.619705] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -3
[  683.619718] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.627697] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -3
[  683.627705] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  683.627717] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.635700] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -7
[  683.635707] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  683.635721] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.643699] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  683.643706] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -5
[  683.643719] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.651705] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  683.651713] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -6
[  683.651726] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.659717] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  683.659726] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -7
[  683.659740] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.667718] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -3
[  683.667726] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -7
[  683.667742] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.675720] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  683.675728] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -5
[  683.675745] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.683711] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -3
[  683.683719] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -5
[  683.683734] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.691717] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  683.691725] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -6
[  683.691741] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.699710] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -7
[  683.699717] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -13
[  683.699731] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.707713] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  683.707720] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -8
[  683.707734] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.715712] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -5
[  683.715719] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -8
[  683.715733] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.723721] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -5
[  683.723729] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -8
[  683.723744] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.731719] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -5
[  683.731727] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  683.731742] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.739713] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -6
[  683.739721] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  683.739734] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.747714] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -6
[  683.747721] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  683.747735] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.755719] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -7
[  683.755727] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  683.755741] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.763718] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -6
[  683.763725] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -10
[  683.763739] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.771722] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -6
[  683.771729] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -9
[  683.771744] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.779723] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -6
[  683.779731] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -8
[  683.779748] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.787711] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -5
[  683.787719] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -8
[  683.787735] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.795728] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  683.795736] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -7
[  683.795753] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.803721] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -4
[  683.803728] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -6
[  683.803742] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.811720] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  683.811727] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -4
[  683.811740] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.819718] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -2
[  683.819726] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -4
[  683.819738] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.827721] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  683.827734] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.835720] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  683.835727] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -2
[  683.835739] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.859733] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: -1
[  683.859740] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: -1
[  683.859756] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  683.987727] evbug.c: Event. Dev: input4, Type: 4, Code: 4, Value: 589825
[  683.987732] evbug.c: Event. Dev: input4, Type: 1, Code: 272, Value: 1
[  683.987759] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.099745] evbug.c: Event. Dev: input4, Type: 4, Code: 4, Value: 589825
[  684.099753] evbug.c: Event. Dev: input4, Type: 1, Code: 272, Value: 0
[  684.099781] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.435574] evbug.c: Event. Dev: input2, Type: 4, Code: 4, Value: 458834
[  684.435585] evbug.c: Event. Dev: input2, Type: 1, Code: 103, Value: 1
[  684.435596] evbug.c: Event. Dev: input2, Type: 0, Code: 0, Value: 0
[  684.571588] evbug.c: Event. Dev: input2, Type: 4, Code: 4, Value: 458834
[  684.571599] evbug.c: Event. Dev: input2, Type: 1, Code: 103, Value: 0
[  684.571610] evbug.c: Event. Dev: input2, Type: 0, Code: 0, Value: 0
[  684.619809] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.619824] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.627806] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  684.627813] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  684.627827] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.635809] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.635823] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.643807] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  684.643814] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 2
[  684.643828] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.651807] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.651820] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.659806] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.659818] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.667808] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.667820] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.675810] evbug.c: Event. Dev: input4, Type: 2, Code: 0, Value: 1
[  684.675817] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.675830] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.683812] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.683826] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.691813] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.691827] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.707815] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.707829] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.723817] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.723831] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.923843] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.923858] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.939842] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.939857] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  684.979843] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  684.979856] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  685.019848] evbug.c: Event. Dev: input4, Type: 2, Code: 1, Value: 1
[  685.019862] evbug.c: Event. Dev: input4, Type: 0, Code: 0, Value: 0
[  685.051636] evbug.c: Event. Dev: input2, Type: 4, Code: 4, Value: 458834
[  685.051647] evbug.c: Event. Dev: input2, Type: 1, Code: 103, Value: 1
[  685.051656] evbug.c: Event. Dev: input2, Type: 0, Code: 0, Value: 0
[  685.171648] evbug.c: Event. Dev: input2, Type: 4, Code: 4, Value: 458834
[  685.171658] evbug.c: Event. Dev: input2, Type: 1, Code: 103, Value: 0
[  685.171668] evbug.c: Event. Dev: input2, Type: 0, Code: 0, Value: 0
[  685.451669] evbug.c: Event. Dev: input2, Type: 4, Code: 4, Value: 458834
[  685.451678] evbug.c: Event. Dev: input2, Type: 1, Code: 103, Value: 1
[  685.451686] evbug.c: Event. Dev: input2, Type: 0, Code: 0, Value: 0
[  685.571689] evbug.c: Event. Dev: input2, Type: 4, Code: 4, Value: 458834
[  685.571699] evbug.c: Event. Dev: input2, Type: 1, Code: 103, Value: 0
[  685.571708] evbug.c: Event. Dev: input2, Type: 0, Code: 0, Value: 0
[  685.947725] evbug.c: Event. Dev: input2, Type: 4, Code: 4, Value: 458792
[  685.947734] evbug.c: Event. Dev: input2, Type: 1, Code: 28, Value: 1
[  685.947744] evbug.c: Event. Dev: input2, Type: 0, Code: 0, Value: 0

```

And then with PeppermintOS

```
peppermint@peppermint ~ $ sudo lsmod
Module                  Size  Used by
ppdev                   5259  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
dm_crypt               11331  0 
snd_hda_codec_realtek   203310  1 
arc4                    1153  2 
snd_hda_intel          21941  1 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2x00usb               9703  1 rt73usb
rt2x00lib              27509  2 rt73usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205146  2 rt2x00usb,rt2x00lib
snd                    54148  14 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126517  2 rt2x00lib,mac80211
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
squashfs               20680  1 
aufs                  149050  1 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  285076  2 
usbhid                 36110  0 
hid                    67032  1 usbhid
usb_storage            39425  1 
drm_kms_helper         29297  1 i915
drm                   162377  3 i915,drm_kms_helper
intel_agp              24119  2 i915
ohci1394               26950  0 
r8169                  34076  0 
ieee1394               81181  1 ohci1394
i2c_algo_bit            5028  1 i915
ahci                   32200  2 
video                  17375  1 i915
mii                     4381  1 r8169
output                  1871  1 video
agpgart                31724  2 drm,intel_agp

```

```
peppermint@peppermint ~ $ sudo lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

```
peppermint@peppermint ~ $ sudo dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-24-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 (Ubuntu 2.6.32-24.39-generic 2.6.32.15+drm33.5)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cf6a0000 (usable)
[    0.000000]  BIOS-e820: 00000000cf6a0000 - 00000000cf6ae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cf6ae000 - 00000000cf6e0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cf6e0000 - 00000000cf700000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001b0000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcf6a0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   2 base 000000000 mask F00000000 write-back
[    0.000000]   3 base 100000000 mask F80000000 write-back
[    0.000000]   4 base 180000000 mask FE0000000 write-back
[    0.000000]   5 base 1A0000000 mask FF0000000 write-back
[    0.000000]   6 base 0CF700000 mask FFFF00000 uncachable
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000cf700000 - 00000000cf800000 (usable) ==> (reserved)
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009b000 (usable)
[    0.000000]  modified: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000cf6a0000 (usable)
[    0.000000]  modified: 00000000cf6a0000 - 00000000cf6ae000 (ACPI data)
[    0.000000]  modified: 00000000cf6ae000 - 00000000cf6e0000 (ACPI NVS)
[    0.000000]  modified: 00000000cf6e0000 - 00000000cf700000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 00000001b0000000 (usable)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 10000-15000
[    0.000000] RAMDISK: 7f331000 - 7fffea25
[    0.000000] Allocated new RAMDISK: 008e0000 - 015ada25
[    0.000000] Move RAMDISK from 000000007f331000 - 000000007fffea24 to 008e0000 - 015ada24
[    0.000000] ACPI: RSDP 000fc440 00014 (v00 HPQOEM)
[    0.000000] ACPI: RSDT cf6a0000 00044 (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: FACP cf6a0200 00084 (v02 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: DSDT cf6a0440 04E91 (v01 HPQOEM SLIC-CPC 00000000 INTL 20051117)
[    0.000000] ACPI: FACS cf6ae000 00040
[    0.000000] ACPI: APIC cf6a0390 0006C (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: MCFG cf6a0400 0003C (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: OEMB cf6ae040 00072 (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: HPET cf6a52e0 00038 (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: GSCI cf6ae0c0 02024 (v01 HPQOEM SLIC-CPC 20090506 MSFT 00000097)
[    0.000000] ACPI: SLIC cf6b00f0 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
[    0.000000] ACPI: SSDT cf6b0bf0 0082F (v01 HPQOEM SLIC-CPC 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2430MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00011000 - 00017f00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009b000 - 0000100000]    BIOS reserved ==> [000009b000 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df65c]              BRK ==> [00008dc000 - 00008df65c]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #7 [00008e0000 - 00015ada25]      NEW RAMDISK ==> [00008e0000 - 00015ada25]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000cf6a0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000cf6a0
[    0.000000] On node 0 totalpages: 849451
[    0.000000] free_area_init_node: node 0, pgdat c0798780, node_mem_map c15af200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4862 pages used for memmap
[    0.000000]   HighMem zone: 617380 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at cf700000 (gap: cf700000:2f700000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s36056 r0 d21288 u1048576
[    0.000000] pcpu-alloc: s36056 r0 d21288 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 842813
[    0.000000] Kernel command line: initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper  quiet splash -- BOOT_IMAGE=/casper/vmlinuz 
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] allocated 16991040 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000cf6a0)
[    0.000000] Memory: 3331212k/3398272k available (4679k kernel code, 65444k reserved, 2116k data, 660k init, 2488968k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591d43 - 0xc07a2e88   (2116 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591d43   (4679 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: PIT calibration matches HPET. 1 loops
[    0.000000] Detected 2599.968 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 5199.93 BogoMIPS (lpj=10399872)
[    0.004019] Security Framework initialized
[    0.004038] AppArmor: AppArmor initialized
[    0.004043] Mount-cache hash table entries: 512
[    0.004159] Initializing cgroup subsys ns
[    0.004163] Initializing cgroup subsys cpuacct
[    0.004166] Initializing cgroup subsys memory
[    0.004172] Initializing cgroup subsys devices
[    0.004174] Initializing cgroup subsys freezer
[    0.004175] Initializing cgroup subsys net_cls
[    0.004194] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004197] CPU: L2 cache: 2048K
[    0.004199] CPU: Physical Processor ID: 0
[    0.004200] CPU: Processor Core ID: 0
[    0.004204] mce: CPU supports 6 MCE banks
[    0.004211] CPU0: Thermal monitoring enabled (TM2)
[    0.004214] using mwait in idle threads.
[    0.004220] Performance Events: Core2 events, Intel PMU driver.
[    0.004227] ... version:                2
[    0.004229] ... bit width:              40
[    0.004230] ... generic registers:      2
[    0.004231] ... value mask:             000000ffffffffff
[    0.004233] ... max period:             000000007fffffff
[    0.004234] ... fixed-purpose events:   3
[    0.004236] ... event mask:             0000000700000003
[    0.004241] Checking 'hlt' instruction... OK.
[    0.022498] ACPI: Core revision 20090903
[    0.032006] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.032011] ftrace: allocating 21780 entries in 43 pages
[    0.040030] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.040387] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.080077] CPU0: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
[    0.084001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 2048K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM2)
[    0.168120] CPU1: Intel Pentium(R) Dual-Core  CPU      E5300  @ 2.60GHz stepping 0a
[    0.168132] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.172017] Brought up 2 CPUs
[    0.172020] Total of 2 processors activated (10203.33 BogoMIPS).
[    0.172482] CPU0 attaching sched-domain:
[    0.172485]  domain 0: span 0-1 level MC
[    0.172487]   groups: 0 1
[    0.172492] CPU1 attaching sched-domain:
[    0.172494]  domain 0: span 0-1 level MC
[    0.172496]   groups: 1 0
[    0.172582] devtmpfs: initialized
[    0.172582] regulator: core version 0.5
[    0.172582] Time: 12:34:16  Date: 11/20/10
[    0.172582] NET: Registered protocol family 16
[    0.172582] Trying to unpack rootfs image as initramfs...
[    0.172582] EISA bus registered
[    0.172582] ACPI: bus type pci registered
[    0.172582] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.172582] PCI: Not using MMCONFIG.
[    0.172582] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.172582] PCI: Using configuration type 1 for base access
[    0.173171] bio: create slab <bio-0> at 0
[    0.173846] ACPI: EC: Look up EC in DSDT
[    0.176694] ACPI: Executed 1 blocks of module-level executable AML code
[    0.180358] ACPI: Interpreter enabled
[    0.180368] ACPI: (supports S0 S1 S3 S4 S5)
[    0.180387] ACPI: Using IOAPIC for interrupt routing
[    0.180429] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.182011] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.182013] PCI: Using MMCONFIG for extended config space
[    0.188049] ACPI: No dock devices found.
[    0.188178] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.188253] pci 0000:00:02.0: reg 10 32bit mmio: [0xfe900000-0xfe97ffff]
[    0.188257] pci 0000:00:02.0: reg 14 io port: [0xc080-0xc087]
[    0.188261] pci 0000:00:02.0: reg 18 32bit mmio pref: [0xd0000000-0xdfffffff]
[    0.188265] pci 0000:00:02.0: reg 1c 32bit mmio: [0xfe800000-0xfe8fffff]
[    0.188364] pci 0000:00:1a.0: reg 20 io port: [0xc400-0xc41f]
[    0.188442] pci 0000:00:1a.1: reg 20 io port: [0xc480-0xc49f]
[    0.188521] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe9fec00-0xfe9fefff]
[    0.188581] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.188586] pci 0000:00:1a.7: PME# disabled
[    0.188633] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe9f4000-0xfe9f7fff]
[    0.188683] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.188687] pci 0000:00:1b.0: PME# disabled
[    0.188765] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.188769] pci 0000:00:1c.0: PME# disabled
[    0.188850] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.188854] pci 0000:00:1c.2: PME# disabled
[    0.188922] pci 0000:00:1d.0: reg 20 io port: [0xc800-0xc81f]
[    0.189001] pci 0000:00:1d.1: reg 20 io port: [0xc880-0xc89f]
[    0.189080] pci 0000:00:1d.2: reg 20 io port: [0xcc00-0xcc1f]
[    0.189162] pci 0000:00:1d.3: reg 20 io port: [0xd000-0xd01f]
[    0.189241] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe9ff800-0xfe9ffbff]
[    0.189297] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.189301] pci 0000:00:1d.7: PME# disabled
[    0.189439] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.189443] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.189446] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.189521] pci 0000:00:1f.2: reg 10 io port: [0xd880-0xd887]
[    0.189527] pci 0000:00:1f.2: reg 14 io port: [0xd800-0xd803]
[    0.189533] pci 0000:00:1f.2: reg 18 io port: [0xd480-0xd487]
[    0.189540] pci 0000:00:1f.2: reg 1c io port: [0xd400-0xd403]
[    0.189546] pci 0000:00:1f.2: reg 20 io port: [0xd080-0xd09f]
[    0.189553] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe9ff000-0xfe9ff7ff]
[    0.189592] pci 0000:00:1f.2: PME# supported from D3hot
[    0.189595] pci 0000:00:1f.2: PME# disabled
[    0.189629] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe9ffc00-0xfe9ffcff]
[    0.189645] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.189885] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.189959] pci 0000:02:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
[    0.190005] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfdff0000-0xfdffffff]
[    0.190032] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfebc0000-0xfebdffff]
[    0.190179] pci 0000:02:00.0: supports D1 D2
[    0.190181] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.190194] pci 0000:02:00.0: PME# disabled
[    0.190320] pci 0000:00:1c.2: bridge io port: [0xe000-0xefff]
[    0.190324] pci 0000:00:1c.2: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.190331] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.190373] pci 0000:01:05.0: reg 10 32bit mmio: [0xfeaff000-0xfeafffff]
[    0.190419] pci 0000:01:05.0: supports D1 D2
[    0.190421] pci 0000:01:05.0: PME# supported from D0 D1 D2 D3hot
[    0.190425] pci 0000:01:05.0: PME# disabled
[    0.190464] pci 0000:00:1e.0: transparent bridge
[    0.190470] pci 0000:00:1e.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.190492] pci_bus 0000:00: on NUMA node 0
[    0.190496] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.190602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.190683] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.190728] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.201033] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.201122] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.201209] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.201294] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.201380] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.201469] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.201558] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.201643] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.201740] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.201750] vgaarb: loaded
[    0.201855] SCSI subsystem initialized
[    0.201935] libata version 3.00 loaded.
[    0.202000] usbcore: registered new interface driver usbfs
[    0.202013] usbcore: registered new interface driver hub
[    0.202034] usbcore: registered new device driver usb
[    0.202130] ACPI: WMI: Mapper loaded
[    0.202131] PCI: Using ACPI for IRQ routing
[    0.202285] NetLabel: Initializing
[    0.202286] NetLabel:  domain hash size = 128
[    0.202287] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.202298] NetLabel:  unlabeled traffic allowed by default
[    0.202325] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.202329] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.208252] Switching to clocksource tsc
[    0.209726] AppArmor: AppArmor Filesystem Enabled
[    0.209739] pnp: PnP ACPI init
[    0.209754] ACPI: bus type pnp registered
[    0.211627] pnp: PnP ACPI: found 14 devices
[    0.211629] ACPI: ACPI bus type pnp unregistered
[    0.211633] PnPBIOS: Disabled by ACPI PNP
[    0.211643] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.211650] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.211652] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.211654] system 00:06: ioport range 0x480-0x4bf has been reserved
[    0.211657] system 00:06: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.211659] system 00:06: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.211664] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.211666] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.211670] system 00:09: ioport range 0xa00-0xadf has been reserved
[    0.211675] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
[    0.211679] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.211683] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.211685] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[    0.211688] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.211690] system 00:0d: iomem range 0x100000-0xcf6fffff could not be reserved
[    0.246387] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.246391] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.246397] pci 0000:00:1c.0:   MEM window: 0xf0000000-0xf01fffff
[    0.246401] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0200000-0x000000f03fffff
[    0.246408] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
[    0.246411] pci 0000:00:1c.2:   IO window: 0xe000-0xefff
[    0.246416] pci 0000:00:1c.2:   MEM window: 0xfeb00000-0xfebfffff
[    0.246421] pci 0000:00:1c.2:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.246427] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.246429] pci 0000:00:1e.0:   IO window: disabled
[    0.246434] pci 0000:00:1e.0:   MEM window: 0xfea00000-0xfeafffff
[    0.246438] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.246454] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.246462]   alloc irq_desc for 17 on node -1
[    0.246463]   alloc kstat_irqs on node -1
[    0.246470] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.246475] pci 0000:00:1c.0: setting latency timer to 64
[    0.246484]   alloc irq_desc for 18 on node -1
[    0.246485]   alloc kstat_irqs on node -1
[    0.246488] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.246492] pci 0000:00:1c.2: setting latency timer to 64
[    0.246499] pci 0000:00:1e.0: setting latency timer to 64
[    0.246504] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.246506] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.246508] pci_bus 0000:03: resource 0 io:  [0x1000-0x1fff]
[    0.246510] pci_bus 0000:03: resource 1 mem: [0xf0000000-0xf01fffff]
[    0.246512] pci_bus 0000:03: resource 2 pref mem [0xf0200000-0xf03fffff]
[    0.246514] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.246516] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.246518] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.246520] pci_bus 0000:01: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.246522] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.246523] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffff]
[    0.246557] NET: Registered protocol family 2
[    0.246654] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.246926] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.247406] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.247660] TCP: Hash tables configured (established 131072 bind 65536)
[    0.247662] TCP reno registered
[    0.247753] NET: Registered protocol family 1
[    0.247773] pci 0000:00:02.0: Boot video device
[    0.248061] cpufreq-nforce2: No nForce2 chipset.
[    0.248083] Scanning for low memory corruption every 60 seconds
[    0.248173] audit: initializing netlink socket (disabled)
[    0.248182] type=2000 audit(1290256456.247:1): initialized
[    0.255991] highmem bounce pool size: 64 pages
[    0.255995] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.257186] VFS: Disk quotas dquot_6.5.2
[    0.257232] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.257693] fuse init (API version 7.13)
[    0.257763] msgmni has been set to 1647
[    0.257939] alg: No test for stdrng (krng)
[    0.257980] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.257983] io scheduler noop registered
[    0.257984] io scheduler anticipatory registered
[    0.257986] io scheduler deadline registered
[    0.258017] io scheduler cfq registered (default)
[    0.258150]   alloc irq_desc for 24 on node -1
[    0.258152]   alloc kstat_irqs on node -1
[    0.258162] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.258171] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.258296]   alloc irq_desc for 25 on node -1
[    0.258297]   alloc kstat_irqs on node -1
[    0.258305] pcieport 0000:00:1c.2: irq 25 for MSI/MSI-X
[    0.258314] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.258397] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.258461] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.258544] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.258548] ACPI: Power Button [PWRB]
[    0.258585] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.258586] ACPI: Power Button [PWRF]
[    0.259157] ACPI: SSDT cf6b0270 002B0 (v01 HPQOEM SLIC-CPC 00000011 INTL 20051117)
[    0.259370] processor LNXCPU:00: registered as cooling_device0
[    0.259712] ACPI: SSDT cf6b0730 002B0 (v01 HPQOEM SLIC-CPC 00000012 INTL 20051117)
[    0.259895] processor LNXCPU:01: registered as cooling_device1
[    0.262675] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.263792] brd: module loaded
[    0.264154] loop: module loaded
[    0.264216] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.264538] Fixed MDIO Bus: probed
[    0.264564] PPP generic driver version 2.4.2
[    0.264594] tun: Universal TUN/TAP device driver, 1.6
[    0.264595] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.264655] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.264675] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.264685] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.264688] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.264711] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.264734] ehci_hcd 0000:00:1a.7: debug port 1
[    0.267595] isapnp: Scanning for PnP cards...
[    0.268618] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.268634] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe9fec00
[    0.283409] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.283512] usb usb1: configuration #1 chosen from 1 choice
[    0.283539] hub 1-0:1.0: USB hub found
[    0.283547] hub 1-0:1.0: 4 ports detected
[    0.283602]   alloc irq_desc for 23 on node -1
[    0.283603]   alloc kstat_irqs on node -1
[    0.283609] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.283624] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.283627] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.283654] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.283679] ehci_hcd 0000:00:1d.7: debug port 1
[    0.287570] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.287585] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe9ff800
[    0.311467] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.311580] usb usb2: configuration #1 chosen from 1 choice
[    0.311604] hub 2-0:1.0: USB hub found
[    0.311611] hub 2-0:1.0: 8 ports detected
[    0.311672] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.311688] uhci_hcd: USB Universal Host Controller Interface driver
[    0.311729]   alloc irq_desc for 16 on node -1
[    0.311731]   alloc kstat_irqs on node -1
[    0.311736] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.311744] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.311747] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.311778] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.311810] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000c400
[    0.311884] usb usb3: configuration #1 chosen from 1 choice
[    0.311903] hub 3-0:1.0: USB hub found
[    0.311908] hub 3-0:1.0: 2 ports detected
[    0.311947]   alloc irq_desc for 21 on node -1
[    0.311948]   alloc kstat_irqs on node -1
[    0.311952] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.311956] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.311959] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.311982] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.312009] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000c480
[    0.312083] usb usb4: configuration #1 chosen from 1 choice
[    0.312102] hub 4-0:1.0: USB hub found
[    0.312107] hub 4-0:1.0: 2 ports detected
[    0.312141] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.312146] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.312148] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.312174] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.312194] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000c800
[    0.312262] usb usb5: configuration #1 chosen from 1 choice
[    0.312280] hub 5-0:1.0: USB hub found
[    0.312286] hub 5-0:1.0: 2 ports detected
[    0.312318]   alloc irq_desc for 19 on node -1
[    0.312320]   alloc kstat_irqs on node -1
[    0.312323] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.312328] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.312331] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.312355] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.312382] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c880
[    0.312446] usb usb6: configuration #1 chosen from 1 choice
[    0.312465] hub 6-0:1.0: USB hub found
[    0.312470] hub 6-0:1.0: 2 ports detected
[    0.312506] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.312511] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.312514] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.312543] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.312564] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000cc00
[    0.312632] usb usb7: configuration #1 chosen from 1 choice
[    0.312651] hub 7-0:1.0: USB hub found
[    0.312657] hub 7-0:1.0: 2 ports detected
[    0.312692] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.312697] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.312700] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.312722] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.312743] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d000
[    0.312811] usb usb8: configuration #1 chosen from 1 choice
[    0.312830] hub 8-0:1.0: USB hub found
[    0.312835] hub 8-0:1.0: 2 ports detected
[    0.312914] PNP: No PS/2 controller found. Probing ports directly.
[    0.315383] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.315388] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.315486] mice: PS/2 mouse device common for all mice
[    0.315580] rtc_cmos 00:03: RTC can wake from S4
[    0.315610] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.315635] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.315718] device-mapper: uevent: version 1.0.3
[    0.356645] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.403430] device-mapper: multipath: version 1.1.0 loaded
[    0.403434] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.440309] EISA: Probing bus 0 at eisa.0
[    0.440316] Cannot allocate resource for EISA slot 1
[    0.440334] EISA: Detected 0 cards.
[    0.444430] Freeing initrd memory: 13110k freed
[    0.450549] cpuidle: using governor ladder
[    0.450552] cpuidle: using governor menu
[    0.450981] TCP cubic registered
[    0.451105] NET: Registered protocol family 10
[    0.451526] lo: Disabled Privacy Extensions
[    0.451792] NET: Registered protocol family 17
[    0.452371] Using IPI No-Shortcut mode
[    0.452464] PM: Resume from disk failed.
[    0.452476] registered taskstats version 1
[    0.452919]   Magic number: 2:834:582
[    0.452962] pci_bus 0000:03: hash matches
[    0.453005] rtc_cmos 00:03: setting system clock to 2010-11-20 12:34:17 UTC (1290256457)
[    0.453007] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.453008] EDD information not available.
[    0.612417] isapnp: No Plug & Play device found
[    0.612681] Freeing unused kernel memory: 660k freed
[    0.613053] Write protecting the kernel text: 4680k
[    0.613084] Write protecting the kernel read-only data: 1840k
[    0.628113] udev: starting version 151
[    0.667377] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.700067] Linux agpgart interface v0.103
[    0.703150] ahci 0000:00:1f.2: version 3.0
[    0.703167] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.703205]   alloc irq_desc for 26 on node -1
[    0.703207]   alloc kstat_irqs on node -1
[    0.703217] ahci 0000:00:1f.2: irq 26 for MSI/MSI-X
[    0.703227] ahci 0000:00:1f.2: controller can't do SNTF, turning off CAP_SNTF
[    0.703269] ahci: SSS flag set, parallel bus scan disabled
[    0.703313] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    0.703316] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ccc ems sxs 
[    0.703321] ahci 0000:00:1f.2: setting latency timer to 64
[    0.722626] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.722668] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.722745] r8169 0000:02:00.0: setting latency timer to 64
[    0.722874]   alloc irq_desc for 27 on node -1
[    0.722876]   alloc kstat_irqs on node -1
[    0.722911] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    0.723475] eth0: RTL8168c/8111c at 0xf812c000, 00:26:18:32:ea:be, XID 1c4000c0 IRQ 27
[    0.724793]   alloc irq_desc for 20 on node -1
[    0.724795]   alloc kstat_irqs on node -1
[    0.724799] ohci1394 0000:01:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.743515] scsi0 : ahci
[    0.743618] scsi1 : ahci
[    0.743662] scsi2 : ahci
[    0.743873] [drm] Initialized drm 1.1.0 20060810
[    0.743992] scsi3 : ahci
[    0.744077] scsi4 : ahci
[    0.744154] scsi5 : ahci
[    0.744293] ata1: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff100 irq 26
[    0.744296] ata2: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff180 irq 26
[    0.744298] ata3: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff200 irq 26
[    0.744301] ata4: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff280 irq 26
[    0.744304] ata5: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff300 irq 26
[    0.744306] ata6: SATA max UDMA/133 abar m2048@0xfe9ff000 port 0xfe9ff380 irq 26
[    0.744398] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    0.744961] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[    0.755986] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    0.781484] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[feaff000-feaff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    0.815034] usb 1-1: configuration #1 chosen from 1 choice
[    0.821252] Initializing USB Mass Storage driver...
[    0.821345] scsi6 : SCSI emulation for USB Mass Storage devices
[    0.821412] usbcore: registered new interface driver usb-storage
[    0.821414] USB Mass Storage support registered.
[    0.821419] usb-storage: device found at 2
[    0.821420] usb-storage: waiting for device to settle before scanning
[    1.040016] usb 2-2: new high speed USB device using ehci_hcd and address 2
[    1.068026] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.068765] ata1.00: ATA-8: WDC WD6400AAKS-65A7B2, 01.03B01, max UDMA/133
[    1.068770] ata1.00: 1250263728 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.069664] ata1.00: configured for UDMA/133
[    1.084167] scsi 0:0:0:0: Direct-Access     ATA      WDC WD6400AAKS-6 01.0 PQ: 0 ANSI: 5
[    1.084312] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.084326] sd 0:0:0:0: [sda] 1250263728 512-byte logical blocks: (640 GB/596 GiB)
[    1.084389] sd 0:0:0:0: [sda] Write Protect is off
[    1.084391] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.084409] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.084518]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.156393] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.172978] usb 2-2: configuration #1 chosen from 1 choice
[    1.173938] scsi7 : SCSI emulation for USB Mass Storage devices
[    1.174035] usb-storage: device found at 2
[    1.174037] usb-storage: waiting for device to settle before scanning
[    1.284019] usb 2-8: new high speed USB device using ehci_hcd and address 3
[    1.577613] usb 2-8: configuration #1 chosen from 1 choice
[    1.808028] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.808250] ata2.00: ATAPI: ATAPI   DVD A  DH16A6L-C, ZHCH, max UDMA/100
[    1.808941] ata2.00: configured for UDMA/100
[    1.816017] usb 3-2: new low speed USB device using uhci_hcd and address 2
[    1.825085] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH16A6L-C ZHCH PQ: 0 ANSI: 5
[    1.830639] sr0: scsi3-mmc drive: 40x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.830644] Uniform CD-ROM driver Revision: 3.20
[    1.830793] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.830861] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.996930] usb 3-2: configuration #1 chosen from 1 choice
[    2.007982] usbcore: registered new interface driver hiddev
[    2.023123] input: CHICONY HP USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input3
[    2.023185] generic-usb 0003:04F2:0841.0001: input,hidraw0: USB HID v1.11 Keyboard [CHICONY HP USB Multimedia Keyboard] on usb-0000:00:1a.0-2/input0
[    2.048156] input: CHICONY HP USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.1/input/input4
[    2.048234] generic-usb 0003:04F2:0841.0002: input,hiddev96,hidraw1: USB HID v1.11 Device [CHICONY HP USB Multimedia Keyboard] on usb-0000:00:1a.0-2/input1
[    2.048249] usbcore: registered new interface driver usbhid
[    2.048251] usbhid: v2.6:USB HID core driver
[    2.060181] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001ec8b10]
[    2.148025] ata3: SATA link down (SStatus 0 SControl 300)
[    2.240015] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    2.415137] usb 4-1: configuration #1 chosen from 1 choice
[    2.433305] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input5
[    2.433372] generic-usb 0003:046D:C062.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1a.1-1/input0
[    2.484025] ata4: SATA link down (SStatus 0 SControl 300)
[    2.820023] ata5: SATA link down (SStatus 0 SControl 300)
[    3.156022] ata6: SATA link down (SStatus 0 SControl 300)
[    3.186370] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.186375] i915 0000:00:02.0: setting latency timer to 64
[    3.189156] mtrr: type mismatch for d0000000,10000000 old: write-back new: write-combining
[    3.189159] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    3.189206]   alloc irq_desc for 28 on node -1
[    3.189208]   alloc kstat_irqs on node -1
[    3.189215] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    3.189221] [drm] set up 7M of stolen space
[    3.189630] [drm] initialized overlay support
[    3.352240] fb0: inteldrmfb frame buffer device
[    3.352243] registered panic notifier
[    3.352292] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    3.353774] vga16fb: initializing
[    3.353777] vga16fb: mapped to 0xc00a0000
[    3.353779] vga16fb: not registering due to another framebuffer present
[    3.454526] Console: switching to colour frame buffer device 128x48
[    4.029847] xor: automatically using best checksumming function: pIII_sse
[    4.047994]    pIII_sse  :  9929.000 MB/sec
[    4.047995] xor: using function: pIII_sse (9929.000 MB/sec)
[    4.050061] device-mapper: dm-raid45: initialized v0.2594b
[    4.733000] EXT4-fs (sda5): mounted filesystem with ordered data mode
[    5.820183] usb-storage: device scan complete
[    5.825191] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[    5.830056] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[    5.834930] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[    5.839817] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[    5.840247] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    5.840351] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    5.840447] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    5.840542] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    5.846029] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    5.846897] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    5.847773] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    5.848653] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    6.172136] usb-storage: device scan complete
[    6.172637] scsi 7:0:0:0: Direct-Access     SanDisk  Cruzer           7.01 PQ: 0 ANSI: 0 CCS
[    6.173415] sd 7:0:0:0: Attached scsi generic sg6 type 0
[    6.173598] sd 7:0:0:0: [sdf] 7905279 512-byte logical blocks: (4.04 GB/3.76 GiB)
[    6.174103] sd 7:0:0:0: [sdf] Write Protect is off
[    6.174108] sd 7:0:0:0: [sdf] Mode Sense: 45 00 00 08
[    6.174112] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[    6.175854] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[    6.175859]  sdf: sdf1
[    6.178094] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[    6.178097] sd 7:0:0:0: [sdf] Attached SCSI removable disk
[    7.193009] aufs 2-standalone.tree-20091207
[    7.202613] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[   13.018685] Adding 15878136k swap on /dev/sda6.  Priority:-1 extents:1 across:15878136k 
[   13.026091] udev: starting version 151
[   13.261689] cfg80211: Calling CRDA to update world regulatory domain
[   13.422507] r8169: eth0: link down
[   13.422696] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.490970] cfg80211: World regulatory domain updated:
[   13.490973] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.490976] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.490978] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.490980] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.490981] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.490983] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.694353]   alloc irq_desc for 22 on node -1
[   13.694356]   alloc kstat_irqs on node -1
[   13.694361] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.694430] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.722788] phy0: Selected rate control algorithm 'minstrel'
[   13.723422] Registered led device: rt73usb-phy0::radio
[   13.723435] Registered led device: rt73usb-phy0::assoc
[   13.723449] Registered led device: rt73usb-phy0::quality
[   13.723960] usbcore: registered new interface driver rt73usb
[   13.784727] rt73usb 2-8:1.0: firmware: requesting rt73.bin
[   13.808671] hda_codec: ALC1200: BIOS auto-probing.
[   13.810014] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   13.940622] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.701051] lp: driver loaded but no devices found
[   14.715181] ppdev: user-space parallel port driver
[   17.061808] CPU0 attaching NULL sched-domain.
[   17.061813] CPU1 attaching NULL sched-domain.
[   17.108078] CPU0 attaching sched-domain:
[   17.108081]  domain 0: span 0-1 level MC
[   17.108083]   groups: 0 1
[   17.108088] CPU1 attaching sched-domain:
[   17.108090]  domain 0: span 0-1 level MC
[   17.108091]   groups: 1 0
[   34.996013] wlan0: deauthenticating from 00:15:6d:80:f1:16 by local choice (reason=3)
[   35.010120] wlan0: direct probe to AP 00:15:6d:80:f0:37 (try 1)
[   35.012382] wlan0: direct probe responded
[   35.012385] wlan0: authenticate with AP 00:15:6d:80:f0:37 (try 1)
[   35.015755] wlan0: authenticated
[   35.015782] wlan0: associate with AP 00:15:6d:80:f0:37 (try 1)
[   35.042264] wlan0: RX AssocResp from 00:15:6d:80:f0:37 (capab=0x421 status=0 aid=1)
[   35.042269] wlan0: associated
[   35.055315] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   45.800008] wlan0: no IPv6 routers present
[   50.104030] wlan0: deauthenticating from 00:15:6d:80:f0:37 by local choice (reason=3)
[   50.128392] wlan0: deauthenticating from 00:15:6d:80:f0:37 by local choice (reason=3)
[   50.139754] wlan0: direct probe to AP 00:15:6d:80:f0:3a (try 1)
[   50.147513] wlan0: direct probe responded
[   50.147519] wlan0: authenticate with AP 00:15:6d:80:f0:3a (try 1)
[   50.161765] wlan0: authenticated
[   50.161784] wlan0: associate with AP 00:15:6d:80:f0:3a (try 1)
[   50.189271] wlan0: RX AssocResp from 00:15:6d:80:f0:3a (capab=0x421 status=0 aid=1)
[   50.189274] wlan0: associated
[   75.493986] EXT4-fs (sda5): mounted filesystem with ordered data mode
```


Hope all of that helps. I tried using the drivers from the manufacturer a few days ago but as chili555 can tell you, that didn't go over well. Nuked my wireless completely.

The wireless in Ubuntu is extremely slow, the download speed is usually no more than 20kbps. DNS is slow. But on PeppermintOS the download speed is 200kbps plus, with very fast DNS.

---

### Post by Alan|Cvette on 2010-11-20
I almost don't want to speak too soon, but uninstalling avahi-daemon not only seems to have made the computer more responsive, but the DNS is extremely fast now, and the internet seems more stable. I will keep you posted!

---

### Post by puppywhacker on 2010-11-25
Sorry for the late response,

So your module on both systems is rt73usb, the version on Ubuntu is bigger, but you get that with different kernel versions. The newer the module the better, so update frequently, if your system doesn't do that automatically you can do it with.

```
sudo apt-get update
sudo apt-get upgrade
```

Anyway, good that you figured out that DNS is the slowest of them all. I'm not a big fan of Avahi since it is difficult to control, if it works, it's perfect, if it doesn't goodluck ...

The main files to see how the DNS resolver is used is with
```
cat /etc/nsswitch.conf
cat /etc/resolv.conf

```

Either way, good job on the troubleshooting =)

---

### Post by Alan|Cvette on 2010-12-07
Sorry for the delay, I had to do some more moving over the week.

Well, the internet is better, but still horrible. I have not been able to update Ubuntu in weeks as the max download speed is bytes to maybe 3kbps if I'm lucky. Getting to this website took 47 seconds, and once the page was up it took an additional 32 seconds for the posts (yes, the text) to load.

I am at my wits end here, it's just fine in Windows but near-unusable here.

---

### Post by Alan|Cvette on 2010-12-09
Bump.

---

### Post by Alan|Cvette on 2010-12-10
Bump.

---

### Post by Alan|Cvette on 2010-12-14
Bump :(

---

### Post by Plumtreed on 2010-12-14
Is it faster or ok with Peppermint???

---

### Post by Alan|Cvette on 2010-12-14
MUCH faster, a consistent 300kbps download speed. DNS is extremely fast. I even tried with Jolicloud too, much faster than Ubuntu. This is driving me crazy. I do love Ubuntu but most of everything I do, I do online, which forces me to switch back to Windows most of the time.

---

### Post by Alan|Cvette on 2010-12-14
If it's of any help, the internet seems to be more responsive and faster when using the live-CD of Ubuntu.

---

### Post by Plumtreed on 2010-12-15
Since we use Peppermint One on our Laptop and Peppermint Ice on our
eeePC the answer is clear, you should use Peppermint.

We do use Ubuntu on the Desktop but do not have your problem but I have read, in passing, that some have had the problem you describe.

I have been trying to locate the posts without much luck but I recall reading about the problem. Have you maintained your updates or has that been too slow? It may have been corrected by now.

---

### Post by Alan|Cvette on 2010-12-15
Yes, I update as often as I can. I usually have to leave it over night though as the download speed can be bytes, to maybe 3kbps if I'm lucky.

---

### Post by Alan|Cvette on 2010-12-18
UPDATE: I followed the steps here [http://usingnix.wordpress.com/2010/10/17/ubuntu-10-10-slow-internet/](http://usingnix.wordpress.com/2010/10/17/ubuntu-10-10-slow-internet/) to disable Ipv6 in grub, and now get a healthy 600kbps download speed. DNS seems faster. I will let everyone know if it goes back to being slow.

---

### Post by Alan|Cvette on 2010-12-21
Improved speed even more by following the steps here to disable power management for the wireless card [http://ubuntuforums.org/archive/index.php/t-1615318.html](http://ubuntuforums.org/archive/index.php/t-1615318.html)

---

### Post by Alan|Cvette on 2011-01-04
Finally solved by following the steps here - [http://forums.linuxmint.com/viewtopic.php?f=150&t=61685&p=354142&hilit=8168#p354142](http://forums.linuxmint.com/viewtopic.php?f=150&t=61685&p=354142&hilit=8168#p354142)

The internet is now 4x faster than Vista.

---

### Post by hugmenot on 2011-01-05
Wingo Way?

---

### Post by Alan|Cvette on 2011-01-07
-delete-

---

