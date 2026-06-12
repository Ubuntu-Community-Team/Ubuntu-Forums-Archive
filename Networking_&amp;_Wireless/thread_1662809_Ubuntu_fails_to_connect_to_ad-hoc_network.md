---
title: "Ubuntu fails to connect to ad-hoc network"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by Rexley on 2011-01-08
Hello guys, I just did a fresh install of ubuntu 10.10 desktop edition 64-bit on my laptop after all the nice comments I read about it, and I've run into some issues with wireless already.

I created an ad-hoc network on my windows 7 pc, with no security options enabled.

My problem is that I can connect just fine using my iPhone, I can connect just fine using windows7 on the same laptop, but I can't connect using ubuntu.

It can see the network, it tries to connect, and after ~1min it disconnects.

I don't understand what the problem is, and I didn't manage to find any solution either googling or searching in the forums.

The only thing I'm not sure about is if it's only my ad-hoc that it can't connect to, or if the wireless generally can't connect to any network, because there aren't any unlocked wireless networks around to test.

Some info:

The laptop is an Acer Aspire 5920g.

Ubuntu 10.10 desktop edition 64-bit
2.6.35-24-generic x86_64


**lspci output:**
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8600M GS] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```**lsusb output:**
```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:0737 Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```**ifconfig output:**
```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:39:1e:b7  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe39:1eb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1045101 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1145081 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67568184 (67.5 MB)  TX bytes:1729350537 (1.7 GB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:843 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5470109 (5.4 MB)  TX bytes:5470109 (5.4 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:04:ca:8c  
          inet6 addr: fe80::21f:3cff:fe04:ca8c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:11004 (11.0 KB)
```[B]
iwconfig output:[/B]
```
lo          no wireless extensions.

eth0      no wireless extensions.

wlan0    IEEE 802.11abg  ESSID:off/any  
            Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:off
```**lsmod output:**
```
Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_realtek   299844  1 
nvidia              10221046  40 
joydev                 11395  0 
snd_hda_intel          26019  2 
arc4                    1497  2 
snd_hda_codec         100919  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
iwl3945                97307  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
iwlcore               146875  1 iwl3945
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              266625  2 iwl3945,iwlcore
r852                   11348  0 
sm_common               4441  1 r852
nand                   38430  2 r852,sm_common
nand_ids                4443  1 nand
nand_ecc                4406  1 nand
video                  22176  0 
uvcvideo               62379  0 
output                  2527  1 video
psmouse                62080  0 
mtd                    21479  2 sm_common,nand
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
serio_raw               4910  0 
intel_agp              32462  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
cfg80211              170293  3 iwl3945,iwlcore,mac80211
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42062  0 
firewire_ohci          24615  0 
hid                    84710  1 usbhid
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
tg3                   135768  0 
```Thanks for your time, peace!  :)

---

### Post by exploitations on 2011-02-22
It seems like no one is answering these questions. I have the same issue, and I cannot find any help online of the forums.

---

### Post by z_kvn on 2011-03-06
Guys I have met exact the same issues here. I tried to follow instructions below which would work under 10.04

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

however I could never get it work under 10.10. This frustrates me a lot. I read somewhere this is related to a bug on the wifi drivers...

So guys let's wait until 11.04 rolls out, peace~~:popcorn:

---

### Post by Rexley on 2011-04-26
That's true, I haven't found any solution 3 months now, and I didn't manage to get any answers. 

I don't consider myself a newbie when it comes to computers, but I'm not an expert either. 

Bottom line is, the problem still remains, and no help from anywhere, or at least hints to testing or trying something different.

:(

---

### Post by collisionystm on 2011-04-26
Maybe make the Ad-Hoc on your ubuntu machine and see if Win 7 can connect to that.

Its all a conspiracy!

---

