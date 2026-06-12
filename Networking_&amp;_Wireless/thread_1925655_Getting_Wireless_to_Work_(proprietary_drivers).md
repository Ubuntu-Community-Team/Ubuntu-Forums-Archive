---
title: "Getting Wireless to Work (proprietary drivers)"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by andyhowington on 2012-02-14
[SIZE="1"]*Sorry, I know there are dozens of threads titled "no proprietary drivers are in use on this system," but none of them answered my question. Most of them centered around nVidia drivers.*[/SIZE]

I just installed Ubuntu 10.04 on an Acer Aspire AM3970. I can't for the life of me get the wireless to work. On my old laptop, it worked after I installed the broadcom proprietary driver through the "Hardware Drivers" un Administration. When I open it now, there aren't any drivers to be seen. The code below implies that it is disabled, but i have it enabled by the wireless item in the system tray. Please help! Thanks

```
sudo lshw -C network

  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:fe400000-fe40ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: e0:69:95:c6:92:e6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.106 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e000(size=256) memory:d0004000-d0004fff(prefetchable) memory:d0000000-d0003fff(prefetchable)
```

---

### Post by josephmills on 2012-02-14
> **andyhowington said:**
> I]Sorry, I know there are dozens of threads titled "no proprietary drivers are in use on this system," but none of them answered my question. Most of them centered around nVidia drivers.[/I]

I just installed Ubuntu 10.04 on an Acer Aspire AM3970. I can't for the life of me get the wireless to work. On my old laptop, it worked after I installed the [COLOR="Red"]broadcom proprietary driver[/COLOR] through the "Hardware Drivers" un Administration. When I open it now, there aren't any drivers to be seen. The code below implies that it is disabled, but i have it enabled by the wireless item in the system tray. Please help! Thanks

```
sudo lshw -C network

  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:fe400000-fe40ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: e0:69:95:c6:92:e6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.106 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:e000(size=256) memory:d0004000-d0004fff(prefetchable) memory:d0000000-d0003fff(prefetchable)
```

Hi there from what I see you have a RaLink card and not a broadcom card. Could we please see a little bit more info about you computer? Please open you terminal (ctrl+alt+t) and enter 
```
lspci -nn && lsmod && lsusb && rfkill list all 
```
then paste that all here. 
thanks

---

### Post by inobe on 2012-02-14
:-#duh, desktop, ignore

---

### Post by andyhowington on 2012-02-14
Hey sorry i was confusing. I had a laptop before that had a broadcom wireless card that worked. Now i'm on a desktop.

Here's the info requested Joseph:
```
andy@andy-desktop:~$ lspci -nn && lsmod && lsusb && rfkill list all
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0100] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0102] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c4a] (rev 05)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller [8086:2822] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
Module                  Size  Used by
nls_utf8                1069  0 
isofs                  29250  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203440  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usb_storage            40033  0 
joydev                  8740  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
led_class               2864  0 
psmouse                63677  0 
rt3090sta             674216  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169
Bus 002 Device 003: ID 0bda:0152 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. 
Bus 001 Device 003: ID 0461:4dcb Primax Electronics, Ltd 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by josephmills on 2012-02-14
> **andyhowington said:**
> Hey sorry i was confusing. I had a laptop before that had a broadcom wireless card that worked. Now i'm on a desktop.

Here's the info requested Joseph:
```
andy@andy-desktop:~$ lspci -nn && lsmod && lsusb && rfkill list all
00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0100] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0102] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
00:1c.5 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 6 [8086:1c1a] (rev b5)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1c4a] (rev 05)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA RAID Controller [8086:2822] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
02:00.0 Network controller [0280]: RaLink RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
Module                  Size  Used by
nls_utf8                1069  0 
isofs                  29250  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203440  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usb_storage            40033  0 
joydev                  8740  0 
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
led_class               2864  0 
psmouse                63677  0 
[COLOR="red"]rt3090sta [/COLOR]            674216  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
ahci                   32680  2 
r8169                  34140  0 
mii                     4381  1 r8169
Bus 002 Device 003: ID 0bda:0152 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52f Logitech, Inc. 
Bus 001 Device 003: ID 0461:4dcb Primax Electronics, Ltd 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```



[COLOR="red"]rt3090sta [/COLOR]   this is the driver that you need and it is installed. but yet rfkill is not working so lets try this

```
sudo rmmod rt3090sta
```
then  
```
sudo modprobe rt3090sta
```
then 
```
rfkill list all 
```
paste the out-put of rfkill list all please.

---

### Post by andyhowington on 2012-02-14
> **josephmills said:**
> [COLOR="red"]rt3090sta [/COLOR]   this is the driver that you need and it is installed. but yet rfkill is not working so lets try this

```
sudo rmmod rt3090sta
```
then  
```
sudo modprobe rt3090sta
```
then 
```
rfkill list all 
```
paste the out-put of rfkill list all please.

Done. No out-put:

```
andy@andy-desktop:~$ sudo rmmod rt3090sta
[sudo] password for andy: 
andy@andy-desktop:~$ sudo modprobe rt3090sta
andy@andy-desktop:~$ rfkill list all
andy@andy-desktop:~$
```

---

### Post by josephmills on 2012-02-14
ok lets try this Download this file 


[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb)


open terminal 
```
sudo rmmod rt3090sta
```
```
cd
```
```
cd Downloads
```

```
sudo dpkg -i rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb 
```

then reboot let us know how it goes after reboot if you get nothing please try to paste "you guessed it "
```
rfkill list all
```

---

### Post by andyhowington on 2012-02-14
> **josephmills said:**
> ok lets try this Download this file 


[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.4.0.4-0ubuntu0%7Eppa0_all.deb)


open terminal 
```
sudo rmmod rt3090sta
```
```
cd
```
```
cd Downloads
```

```
sudo dpkg -i rt3090-dkms_2.4.0.4-0ubuntu0~ppa0_all.deb 
```

then reboot let us know how it goes after reboot if you get nothing please try to paste "you guessed it "
```
rfkill list all
```


HA! It works. Thank you so much!!! \\:D/

---

### Post by josephmills on 2012-02-15
> **andyhowington said:**
> HA! It works. Thank you so much!!! \\:D/

Great News Then ! If you could please mark as solved so others can learn from it to thanks. and Have fun ! 

:KS:KS Oh and great Job !:KS:KS

---

