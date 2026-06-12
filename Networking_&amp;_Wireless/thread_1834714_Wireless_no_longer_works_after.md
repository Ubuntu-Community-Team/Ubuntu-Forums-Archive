---
title: "Wireless no longer works after"
date: 2011-08-28
forum: Networking &amp; Wireless
---

### Post by RDn6427 on 2011-08-28
Hello,
     Currently have been using Ubuntu 11.04, I installed Windows 7. Ended up having to use EasyBCD to be able to dualboot Ubuntu and Win7. Problem is now Wifi does not work at all in Ubuntu. Was working perfect before installation of Windows and works perfect when I boot into Windows but no longer works when I boot into Ubuntu. I have been at it for hours just trying and googling solutions online to no success. Wired internet works fine but runs slower. Any help will be appreciated.

info:

reuben@reubhp:~$ cat /etc/lsb-release
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

```reuben@reubhp:~$ lsusb
```

Bus 005 Device 009: ID 1c4f:0003 SiGma Micro HID controller
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:011d Hewlett-Packard Integrated Bluetooth Module
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 125f:312a A-DATA Technology Co., Ltd. 
Bus 001 Device 008: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```reuben@reubhp:~$ lspci
```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
0b:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0b:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0b:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0b:00.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
0b:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0b:03.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)
reuben@reubhp:~$ lspci -nn | grep -i net
0b:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
0b:03.0 Network controller [0280]: Atheros Communications Inc. AR922X Wireless Network Adapter [168c:0029] (rev 01)

```reuben@reubhp:~$ sudo lshw -C network
```

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:a2:85:9f
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.140 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 ioport:5000(size=256) memory:c8217400-c82174ff
  *-network:1 UNCLAIMED
       description: Network controller
       product: AR922X Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 3
       bus info: pci@0000:0b:03.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=64
       resources: memory:c8200000-c820ffff

```reuben@reubhp:~$ lsmod
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  2 
uas                    17676  0 
radeon                900494  1 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   184164  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           13184  1 radeon
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
binfmt_misc            13213  1 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
vboxnetadp             13323  0 
snd_seq_midi_event     14475  1 snd_seq_midi
vboxnetflt             27855  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
vboxdrv               219250  2 vboxnetadp,vboxnetflt
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 37646  8 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_ms                13175  0 
memstick               15816  1 tifm_ms
soundcore              12600  1 snd
pcmcia                 39671  0 
bnep                   17706  2 
btusb                  18160  2 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
hp_wmi                 13418  0 
psmouse                73312  0 
serio_raw              12990  0 
yenta_socket           27230  0 
bluetooth             133200  23 rfcomm,bnep,btusb
sparse_keymap          13666  1 hp_wmi
ndiswrapper           192828  0 
tifm_7xx1              12898  0 
pcmcia_rsrc            18292  1 yenta_socket
lp                     13349  0 
video                  18951  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
tifm_core              15040  2 tifm_ms,tifm_7xx1
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
sdhci_pci              13623  0 
firewire_ohci          31504  0 
8139too                23208  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core

```reuben@reubhp:~$ iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

```reuben@reubhp:~$ ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:c0:9f:a2:85:9f  
          inet addr:192.168.1.140  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fea2:859f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3294841 (3.2 MB)  TX bytes:715588 (715.5 KB)
          Interrupt:20 Base address:0x5000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5024 (5.0 KB)  TX bytes:5024 (5.0 KB)

```reuben@reubhp:~$ sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

```reuben@reubhp:~$ uname -r -m
```

2.6.38-11-generic i686
reuben@reubhp:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```reuben@reubhp:~$ nm-tool
```

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:C0:9F:A2:85:9F

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.140
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             129.250.35.250
    DNS:             129.250.35.251
    DNS:             192.168.1.1

```reuben@reubhp:~$ lsmod | grep b43
```

b43                   311234  0 
ssb                    51021  1 b43
mac80211              259567  1 b43
cfg80211              155552  2 b43,mac80211
pcmcia                 39671  2 b43,ssb
reuben@reubhp:~$ dmesg | grep b43
reuben@reubhp:~$ lsmod
Module                  Size  Used by
b43                   311234  0 
ssb                    51021  1 b43
mac80211              259567  1 b43
cfg80211              155552  2 b43,mac80211
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
usb_storage            43946  2 
uas                    17676  0 
radeon                900494  1 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
drm                   184164  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           13184  1 radeon
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
binfmt_misc            13213  1 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
vboxnetadp             13323  0 
snd_seq_midi_event     14475  1 snd_seq_midi
vboxnetflt             27855  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
vboxdrv               219250  2 vboxnetadp,vboxnetflt
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 37646  8 
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tifm_ms                13175  0 
memstick               15816  1 tifm_ms
soundcore              12600  1 snd
pcmcia                 39671  2 b43,ssb
bnep                   17706  2 
btusb                  18160  2 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
hp_wmi                 13418  0 
psmouse                73312  0 
serio_raw              12990  0 
yenta_socket           27230  0 
bluetooth             133200  23 rfcomm,bnep,btusb
sparse_keymap          13666  1 hp_wmi
ndiswrapper           192828  0 
tifm_7xx1              12898  0 
pcmcia_rsrc            18292  1 yenta_socket
lp                     13349  0 
video                  18951  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
tifm_core              15040  2 tifm_ms,tifm_7xx1
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
sdhci_pci              13623  0 
firewire_ohci          31504  0 
8139too                23208  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
8139cp                 22497  0 
crc_itu_t              12627  1 firewire_core

```reuben@reubhp:~$ cat /etc/modprobe.d/blacklist.conf
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb

```reuben@reubhp:~$ rfkill list all
```

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```

---

### Post by wildmanne39 on 2011-08-28
Hi, please run this command and post the results here:
```
lspci -nn | grep 0280
```
I will help more tomorrow.
Thank you

---

### Post by RDn6427 on 2011-08-28
command results:

reuben@reubhp:~$ lspci -nn | grep 0280
```

0b:03.0 Network controller [0280]: Atheros Communications Inc. AR922X Wireless Network Adapter [168c:0029] (rev 01)

```

and just in case it helps, laptop is zd pavilion zd8000 (ancient, I know...), with this wireless card: TP-LINK TL-WN861N and everything was working fine til I added Win 7.

---

### Post by fdrake on 2011-08-28
> 
....
  *-network:1 [COLOR="Red"]UNCLAIMED[/COLOR]
       description: Network controller
       product: AR922X Wireless Network Adapter

....


what's the
```
sudo lspci -vvvs 0b:03.0
```

---

### Post by bkratz on 2011-08-28
Much I do not understand in the first post! There are two listing of lsmod, the second shows b43,ssb etc. which are not in the first listing at all, and they are not correct for the card anyway, and are also blacklisted. Also ndiswrapper shows up too. Try that one time??  The correct driver for the card is ath9k which is already resident in the kernel and should remove the unclaimed. I think the first step is to try

sudo modprobe ath9k

and rerun the earlier command then see if the unclaimed disappears.

---

### Post by wildmanne39 on 2011-08-28
Hi, after you do as bkratz recommends remove all the broadcom and ndiswrapper drivers, then if you need more help post back.
Thank you

---

### Post by RDn6427 on 2011-08-28
Kk, in japan timezone n currently at work. Will post back when i get home later. Many thanks.

---

### Post by RDn6427 on 2011-08-29
sudo modprobe ath9k

This worked for me, brought all the Wifi functions back. bkratz, many many thanks! Only problem is I have to do this each time after a restart... There something I can do for that?

wildmanne39, I did all that you recommended. Thank you as well for your help.__

---

### Post by praseodym on 2011-08-29
You can force the module to load at boot via:

```
echo ath9k | sudo tee -a /etc/modules
```

---

### Post by RDn6427 on 2011-08-29
praseodym, didn't expect that quick of a response. Thank You! Can't thank all of you enough.

---

### Post by wildmanne39 on 2011-08-29
Hi, I am glad you got it working,  would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

