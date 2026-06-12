---
title: "wireless not working (wlan not found)"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by dencamel on 2011-04-19
Hello,

I have recently bought a new laptop (medion akoya p7618) and I can't get the wireless working... 
With windows 7 it's working.

I followed the sticky guide but still no success....

The problem is in the first place that it doesn't list my wlan :
lspci -nn

```

:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 18)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0df4] (rev a1)
06:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
07:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
08:00.0 Network controller [0280]: Intel Corporation Device [8086:08ae]


```

I also installed the driver but the device is not present

ndiswrapper -l
```
.
netwlv32 : driver installed

```

iwconfig
```

~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

```

Any help is appreciated!

---

### Post by josephmills on 2011-04-19
hi there could we please see a ```
lshw -C network
``` thanks

---

### Post by dencamel on 2011-04-19
> **josephmills said:**
> hi there could we please see a ```
lshw -C network
``` thanks

Yes sure...

```

  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: c0
       serial: 00:26:2d:c5:1e:dd
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.2.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:48 memory:fb400000-fb43ffff ioport:c000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fb200000-fb201fff


```

---

### Post by josephmills on 2011-04-19
could we please see a ```
rfkill list all
``` and a ```
lsmod
``` thanks

---

### Post by dencamel on 2011-04-19
> **josephmills said:**
> could we please see a ```
rfkill list all
``` and a ```
lsmod
``` thanks

rfkill list all

```

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```- lsmod

```

Module                  Size  Used by
ndiswrapper           184384  0 
nls_utf8                1069  1 
isofs                  30022  1 
parport_pc             26378  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_realtek   218492  1 
joydev                  8767  0 
snd_hda_intel          22299  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
i915                  296139  4 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
nouveau               518076  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    56825  1 nouveau
drm_kms_helper         30200  2 i915,nouveau
drm                   168732  6 i915,nouveau,ttm,drm_kms_helper
intel_agp              26926  2 i915
psmouse                59033  0 
serio_raw               4022  0 
acer_wmi               13929  0 
led_class               2633  1 acer_wmi
intel_ips              11101  0 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18712  1 i915
xhci_hcd               54399  0 
output                  1883  1 video
i2c_algo_bit            5168  2 i915,nouveau
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
lp                      7342  0 
agpgart                32075  3 ttm,intel_agp,drm
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36978  0 
hid                    67742  1 usbhid
usb_storage            40236  0 
ahci                   19198  3 
libahci                21792  1 ahci
atl1c                  30173  0 

```

---

### Post by josephmills on 2011-04-19
how about a ```
lsusb
``` I cant seem to see you chipset? anyone else see it? What is the driver that you have right now?

---

### Post by dencamel on 2011-04-19
> **josephmills said:**
> how about a ```
lsusb
``` I cant seem to see you chipset? anyone else see it? What is the driver that you have right now?

-lsusb
```

Bus 002 Device 003: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I have installed the windows driver "netwlv32" with windows wireless drivers... It states that the driver is installed but no hardware is present...

thanks

---

### Post by josephmills on 2011-04-19
I think that this might be it ```
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp.
``` But could be wrong. you are using a usb wifi thingy?

---

### Post by jawilljr on 2011-04-19
I think this is his wifi device:

```
08:00.0 Network controller [0280]: Intel Corporation Device [8086:08ae]
```Which I think translates to this:

[ Intel Centrino Wireless-N 100]("http://pci-ids.ucw.cz/read/PC/8086/08ae")

According to [here]("http://intellinuxwireless.org/") he needs kernel version 2.6.37 or higher...or he could use compat-wireless.

Jerry

---

### Post by josephmills on 2011-04-19
> **jawilljr said:**
> I think this is his wifi device:

```
08:00.0 Network controller [0280]: Intel Corporation Device [8086:08ae]
```Which I think translates to this:

[ Intel Centrino Wireless-N 100]("http://pci-ids.ucw.cz/read/PC/8086/08ae")

According to [here]("http://intellinuxwireless.org/") he needs kernel version 2.6.37 or higher...or he could use compat-wireless.

Jerry

good eye jerry i dont know how I missed that thanks again

---

### Post by dencamel on 2011-04-20
> **jawilljr said:**
> I think this is his wifi device:

```
08:00.0 Network controller [0280]: Intel Corporation Device [8086:08ae]
```Which I think translates to this:

[ Intel Centrino Wireless-N 100]("http://pci-ids.ucw.cz/read/PC/8086/08ae")

According to [here]("http://intellinuxwireless.org/") he needs kernel version 2.6.37 or higher...or he could use compat-wireless.

Jerry

Yes that's correct it's the intel centrino wireless N100... That's what I see under devices in Windows 7.
Is it safe to update the kernel to 2.6.37 or should I wait for the next release of 11.4?

Thanks for your research!
[ ]("http://pci-ids.ucw.cz/read/PC/8086/08ae")

---

