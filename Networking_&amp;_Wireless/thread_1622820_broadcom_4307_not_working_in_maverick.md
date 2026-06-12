---
title: "broadcom 4307 not working in maverick"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by morganpatrick on 2010-11-15
Hi,

I am running Ubuntu 10.10 on a 64 bit machine.

I have a Linksys WMP11 PCI card installed and the wireless doesn't show up, and the proprietary driver doesn't show up either.

I installed b43-fwcutter and wasn't prompted to extract any firmware.

I installed ndiswrapper and manually added all three inf files off the disc. One says hardware is present.

```
~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

```
sudo lshw -C network
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: IPN 2120 802.11b
       vendor: InProComm Inc.
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=32 mingnt=32
       resources: memory:50005800-50005fff
  *-network:1
       description: Ethernet interface
       product: N10/ICH 7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:13:20:6f:ba:94
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=10.0.0.15 latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:50004000-50004fff ioport:1000(size=64)

```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:20:6f:ba:94  
          inet addr:10.0.0.15  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fe6f:ba94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10386294 (10.3 MB)  TX bytes:1148958 (1.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```

```
~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
03:01.0 Ethernet controller: InProComm Inc. IPN 2120 802.11b
03:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
03:08.0 Ethernet controller: Intel Corporation N10/ICH 7 Family LAN Controller (rev 01)
```

```
sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device
```

```
lsmod
Module                  Size  Used by
nls_utf8                1453  1 
isofs                  34218  1 
binfmt_misc             7984  1 
snd_hda_codec_idt      64667  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
i915                  330249  2 
snd_seq_midi_event      7291  1 snd_seq_midi
drm_kms_helper         32836  1 i915
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   206161  3 i915,drm_kms_helper
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
usb_storage            50372  0 
snd                    64117  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           245044  0 
led_class               3393  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
output                  2527  1 video
intel_agp              32080  2 i915
usbhid                 42062  0 
hid                    84678  1 usbhid
ppdev                   6804  0 
parport_pc             30086  1 
lp                     10201  0 
parport                37032  3 ppdev,parport_pc,lp
firewire_ohci          24679  0 
firewire_core          54327  1 firewire_ohci
e100                   34686  0 
mii                     5261  1 e100
crc_itu_t               1739  1 firewire_core
```

I have spent hours trying to get this to work and am at the end of my rope. Please help! thanks.

---

### Post by morganpatrick on 2010-11-18
Anyone? Is there any more information needed to address this problem?

---

### Post by morganpatrick on 2010-11-24
I'm really surprised there's no response to this at all. It seems like getting your wireless card to work is a fairly common Ubuntu problem that other people could relate to. Oh well.

---

### Post by irvotheturbo on 2010-11-25
> **morganpatrick said:**
> 

I have a Linksys WMP11 PCI card installed and the wireless doesn't show up, and the proprietary driver doesn't show up either.

I installed b43-fwcutter and wasn't prompted to extract any firmware.

I installed ndiswrapper and manually added all three inf files off the disc. One says hardware is present.

Looks like we're in the same boat Patrick, although I doubt you are on the right track with your Broadcom chipset. 
I'm guessing you also have a WMP11 v4 card like I do. If so (and it looks like you do: InProComm Inc. IPN 2120), you shouldn't install b43-fwcutter as this is for Broadcom chipsets.

I had no problem installing the drivers for the WMP11 v4 under Ubuntu 32bit. I just installed 64bit today, and no go so far.

Did you have a look at *dmesg |tail*? Mine says this after starting ndiswrapper:

```
$ dmesg |tail
[ 3252.757904] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 3252.779263] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[ 3252.779268] ndiswrapper (load_sys_files:206): couldn't prepare driver 'lsipnds'
[ 3252.779750] ndiswrapper (load_wrap_driver:108): couldn't load driver lsipnds; check system log for messages from 'loadndisdriver'
[ 3252.779855] usbcore: registered new interface driver ndiswrapper

```

Not sure if this card ever got a 64bit driver.

- Irv

---

