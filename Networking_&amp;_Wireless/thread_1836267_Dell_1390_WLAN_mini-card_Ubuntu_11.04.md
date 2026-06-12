---
title: "Dell 1390 WLAN mini-card Ubuntu 11.04"
date: 2011-08-30
forum: Networking &amp; Wireless
---

### Post by aoeuis on 2011-08-30
Hello everyone, Ubuntu 11.04 doesn't recognize the wireless mini-card in my laptop, please help me correct this situation.

Computer: Intel Celeron M CPU
Please ask me for other information that you need to diagnose the situation, thank you in advance.

---

### Post by wildmanne39 on 2011-08-30
Hi, please run these commands:
```
lspci -nn | grep 0280
```
```
sudo lshw -C network 
```
```
iwconfig
```
```
lsmod
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by aoeuis on 2011-09-01
Here you go

lspci -nn | grep 0280

```

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```sudo lshw -C network
```

PCI (sysfs)  

  *-network               

       description: Network controller

       product: BCM4311 802.11b/g WLAN

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:0c:00.0

       version: 01

       width: 32 bits

       clock: 33MHz

       capabilities: pm msi pciexpress bus_master cap_list

       configuration: driver=b43-pci-bridge latency=0

       resources: irq:17 memory:dfdfc000-dfdfffff

  *-network

       description: Ethernet interface

       product: BCM4401-B0 100Base-TX

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 02

       serial: 00:15:c5:64:36:e9

       size: 10Mbit/s

       capacity: 100Mbit/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s

       resources: irq:17 memory:df9fe000-df9fffff

  *-network DISABLED

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:16:ce:8f:99:e5

       capabilities: ethernet physical wireless

       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg


```iwconfig
```

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

```lsmod
```

Module                  Size  Used by

nls_iso8859_1          12617  1 

nls_cp437              12751  1 

vfat                   17335  1 

fat                    55505  1 vfat

parport_pc             32111  0 

ppdev                  12849  0 

binfmt_misc            13213  1 

snd_hda_codec_idt      60537  1 

snd_hda_intel          24140  2 

snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel

arc4                   12473  2 

snd_hwdep              13274  1 snd_hda_codec

snd_pcm                80244  2 snd_hda_intel,snd_hda_codec

i915                  450944  3 

snd_seq_midi           13132  0 

b43                   296610  0 

snd_rawmidi            25269  1 snd_seq_midi

snd_seq_midi_event     14475  1 snd_seq_midi

mac80211              257001  1 b43

snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event

snd_timer              28659  2 snd_pcm,snd_seq

joydev                 17322  0 

drm_kms_helper         40745  1 i915

snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq

r852                   17878  0 

drm                   180037  4 i915,drm_kms_helper

dell_laptop            13515  0 

sm_common              16737  1 r852

nand                   49822  2 r852,sm_common

nand_ids                8547  1 nand

cfg80211              156212  2 b43,mac80211

dcdbas                 14054  1 dell_laptop

nand_ecc               13070  1 nand

snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

psmouse                73312  0 

mtd                    26720  2 sm_common,nand

i2c_algo_bit           13184  1 i915

serio_raw              12990  0 

soundcore              12600  1 snd

video                  18951  1 i915

snd_page_alloc         14073  2 snd_hda_intel,snd_pcm

lp                     13349  0 

parport                36746  3 parport_pc,ppdev,lp

mmc_block              17704  2 

b44                    35301  0 

firewire_ohci          31504  0 

usb_storage            43946  1 

sdhci_pci              13623  0 

firewire_core          56138  1 firewire_ohci

uas                    17676  0 

ssb                    45942  2 b43,b44

sdhci                  22720  1 sdhci_pci

crc_itu_t              12627  1 firewire_core


```rfkill list all
```

0: dell-wifi: Wireless LAN

    Soft blocked: no

    Hard blocked: no

1: phy0: Wireless LAN

    Soft blocked: no

    Hard blocked: no

```

---

### Post by bkratz on 2011-09-01
Please read this, it is about your wireless card

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)


Sorry finally read the whole thing and it looks like you already have b43.

---

### Post by praseodym on 2011-09-01
Hi,

you need the firmware for your b43 driver:

```
sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
```

---

### Post by wildmanne39 on 2011-09-01
Hi, if you still have problems after installing the firmware post back sometimes there is a problem with systems that have a broadcom wireless and broadcom ethernet like you do.
Thank you

---

### Post by aoeuis on 2011-09-01
Thanks, everyone, for your help. The fix worked, and I was able to "connect" to my wireless network, however even after "connecting to it" (entering wireless password and keyring password) I was still unable to access the internet. The network icon to the right of the keyboard icon on the top-bar is spinning, and disconnects after a while, which leads me to think that it didn't actually establish connection.

Under network connections, I didn't see any auto-wireless or anything similar. Auto-ethernet (though usb 2.0 lan adapter) works fine, although inserting the internet-cable head into the computer's own port doesn't seem to do anything...

---

### Post by nm_geo on 2011-09-01
> **aoeuis said:**
> Thanks, everyone, for your help. The fix worked, and I was able to "connect" to my wireless network, however even after "connecting to it" (entering wireless password and keyring password) I was still unable to access the internet. The network icon to the right of the keyboard icon on the top-bar is spinning, and disconnects after a while, which leads me to think that it didn't actually establish connection.

Under network connections, I didn't see any auto-wireless or anything similar. Auto-ethernet (though usb 2.0 lan adapter) works fine, although inserting the internet-cable head into the computer's own port doesn't seem to do anything...

Let's look at blacklist issues

```
grep -e b43 -e ssb /etc/modprobe.d/*
```

Then kernel messages

```
dmesg | egrep 'b43|irmware|ssb'
```

---

### Post by aoeuis on 2011-09-01
blacklist
```

/etc/modprobe.d/blacklist.conf:# replaced by b43 and ssb. 

```kernel
```

 [    1.500625] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [    1.500640] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64 
 [    1.520321] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243) 
 [    1.520339] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243) 
 [    1.520355] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243) 
 [    1.520370] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243) 
 [    1.560146] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0 
 [    1.632054] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243) 
 [    1.632064] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243) 
 [    1.632073] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243) 
 [    1.672229] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0 
 [    1.693403] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:64:36:e9 
 [   13.005445] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work. 
 [   15.145954] b43-phy0: Broadcom 4311 WLAN found (core revision 10) 
 [   15.639683] Registered led device: b43-phy0::tx 
 [   15.639715] Registered led device: b43-phy0::rx 
 [   15.639750] Registered led device: b43-phy0::radio 
 [   15.639778] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ] 
 [   30.932055] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10) 
 
```maybe
```

Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work. 

```that part was the problem...

---

### Post by nm_geo on 2011-09-01
> maybe
     Code:
     Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work. 
that part was the problem...I would not think that would be a problem with wireless or ethernet.  Now as I read earlier you can not get an internal wired connection or wireless correct? But you are connecting with ethernet adapter correct?
With ethernet adapter working do this gets you current with Natty.
 
```
sudo apt-get update && sudo apt-get upgrade
```Have we tried 

```
sudo modprobe b43
```If not go for it .. It might tickle that driver into working.

then another 
```

sudo lshw -C network
```

---

### Post by aoeuis on 2011-09-01
update

```

The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic

```I'm pretty sure that is not related

    sudo modprobe b43
then 

sudo lshw -C network
```

PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:dfdfc000-dfdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:64:36:e9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:df9fe000-df9fffff
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:8f:99:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 00:90:cc:e7:9d:99
       size: 100Mbit/s
       capacity: 100Mbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=192.168.2.16 link=yes multicast=yes port=MII speed=100Mbit/s

```Let me try after rebooting...

---

### Post by nm_geo on 2011-09-01
Sorry. should have asked for this one too

```
nm-tool
```If you don't already have nm-tool  follow the apt-get instructions and get it .. Then run the command.

[SIZE=3]**Be sure to reboot without the USB adapter plugged in...**[/SIZE]

---

### Post by wildmanne39 on 2011-09-01
Hi, good to see you nm_geo since you are here I will let you take care of it.

---

### Post by nm_geo on 2011-09-01
> **wildmanne39 said:**
> Hi, good to see you nm_geo since you are here I will let you take care of it.
No problem we are a good team..:P
He is soo sooo close maybe you will spot something i am missing ..
He has no blacklist problems ..the firmware installed correctly.. the dmesg looks like mine all clear there..

The wired USB adapter might be the wireless problem.. or his set-up in the nm-applet,

---

### Post by aoeuis on 2011-09-01
nm-tool

```

NetworkManager Tool

State: connected

- Device: wlan0  [Wireless connection 1] ---------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:16:CE:8F:99:E5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    TRENDnet652:     Infra, 00:14:D1:4E:8A:5B, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA
    Pillow:          Infra, 00:13:F7:B8:20:84, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA
    strick:          Infra, E0:91:F5:02:24:32, Freq 2422 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    BELL931:         Infra, 98:2C:BE:62:F2:D1, Freq 2452 MHz, Rate 54 Mb/s, Strength 44 WEP
    BELL960:         Infra, 3C:EA:4F:30:44:81, Freq 2422 MHz, Rate 54 Mb/s, Strength 95 WEP
    Kinley :         Infra, 00:22:15:A8:70:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA
    WLAN:            Infra, 90:E6:BA:7D:43:FE, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA
    sky blue:        Infra, 94:44:52:2C:A7:D0, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA
    CK_Milner:       Infra, 00:22:2D:7D:FD:36, Freq 2457 MHz, Rate 54 Mb/s, Strength 50 WPA
    do not touch me, jackass: Infra, E0:69:95:A4:9B:A0, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    whatsoever:      Infra, 00:22:2D:CE:39:E1, Freq 2432 MHz, Rate 54 Mb/s, Strength 50 WPA
    BELL623:         Infra, 3C:EA:4F:D9:B7:C9, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WEP
    BELL550:         Infra, 64:0F:28:34:70:09, Freq 2427 MHz, Rate 54 Mb/s, Strength 51 WEP
    Lovers & Other Strangers: Infra, 34:EF:44:9E:12:39, Freq 2442 MHz, Rate 54 Mb/s, Strength 50 WEP
    EDSCanada:       Infra, 00:0F:66:1A:95:E7, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WEP
    P.A.K:           Infra, 00:14:D1:BA:20:6A, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    BrownOak:        Infra, 38:60:77:07:C6:90, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    Quazgar:         Infra, 98:FC:11:54:06:91, Freq 2452 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    BELL130:         Infra, 3C:EA:4F:0A:48:39, Freq 2442 MHz, Rate 54 Mb/s, Strength 58 WEP
    chefnet:         Infra, 00:26:F3:9A:9A:41, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WPA
    Zebenzki:        Infra, B8:C7:5D:02:A9:A9, Freq 2427 MHz, Rate 54 Mb/s, Strength 54 WPA2
    hpsetup:         Ad-Hoc, DE:D3:85:C7:CB:8A, Freq 2437 MHz, Rate 11 Mb/s, Strength 54
    WLAN:            Infra, 00:22:2D:3A:7F:E0, Freq 2462 MHz, Rate 54 Mb/s, Strength 44
    BELL365:         Infra, 00:1D:5A:77:EE:C9, Freq 2447 MHz, Rate 54 Mb/s, Strength 47 WEP
    BELL754:         Infra, 64:0F:28:0A:05:49, Freq 2437 MHz, Rate 54 Mb/s, Strength 44 WEP
    BELL670:         Infra, 00:26:50:41:28:69, Freq 2452 MHz, Rate 54 Mb/s, Strength 55 WEP
    BELL700:         Infra, 00:25:3C:F3:61:09, Freq 2422 MHz, Rate 54 Mb/s, Strength 58 WEP
    blessuass:       Infra, 00:26:F3:2B:A7:39, Freq 2427 MHz, Rate 54 Mb/s, Strength 44 WPA
    janice:          Infra, 00:26:F3:2A:D8:01, Freq 2457 MHz, Rate 54 Mb/s, Strength 50 WPA
    belkin54g:       Infra, 00:1C:DF:99:88:06, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    CcNet:           Infra, 00:22:2D:16:40:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA
    HOME WIRELESS:   Infra, B0:E7:54:2A:71:71, Freq 2457 MHz, Rate 54 Mb/s, Strength 47 WPA
    yuannauy:        Infra, E0:69:95:7F:B3:DB, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    ME-WIRELESS:     Infra, 00:22:2D:CC:5D:79, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA
    BELLinternet:    Infra, C0:83:0A:D8:61:79, Freq 2417 MHz, Rate 54 Mb/s, Strength 55 WPA
    WLAN:            Infra, 70:71:BC:CF:F8:54, Freq 2462 MHz, Rate 54 Mb/s, Strength 77
    BELL291:         Infra, 00:1B:5B:D5:9F:09, Freq 2447 MHz, Rate 54 Mb/s, Strength 47 WEP
    Siva:            Infra, 00:1B:5B:8C:6C:D1, Freq 2457 MHz, Rate 54 Mb/s, Strength 54 WEP
    BB:              Infra, 00:26:50:2A:07:D9, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WEP
    Xuan:            Infra, 00:24:01:77:09:A5, Freq 2437 MHz, Rate 54 Mb/s, Strength 58 WEP
    807:             Infra, 00:22:2D:1D:10:19, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WEP
    Michelle H:      Infra, 00:23:51:AA:CE:91, Freq 2447 MHz, Rate 54 Mb/s, Strength 82 WEP
    BELL729:         Infra, 3C:EA:4F:1D:75:51, Freq 2432 MHz, Rate 54 Mb/s, Strength 95 WEP
    FahadS.com:      Infra, 00:13:F7:AB:F2:B4, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA
    GJY:             Infra, 00:22:2D:6C:68:31, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    CTS:             Infra, 00:25:86:B9:D2:30, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA
    NightSpot Inc:   Infra, 00:18:E7:E5:D9:E4, Freq 2432 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    WLAN:            Infra, 00:13:F7:B8:58:82, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA
    LondonHeatingAir:Infra, 00:26:F3:32:B7:34, Freq 2457 MHz, Rate 54 Mb/s, Strength 51 WPA
    PJSFinancial:    Infra, 00:24:56:BC:FF:21, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA
    tkpk:            Infra, 00:22:2D:A1:0A:61, Freq 2417 MHz, Rate 54 Mb/s, Strength 70 WPA
    Sirous:          Infra, 00:24:8C:61:3E:EE, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA
    GIRLSNET:        Infra, 00:22:2D:C9:05:05, Freq 2457 MHz, Rate 54 Mb/s, Strength 58 WPA
    TK:              Infra, 00:25:9C:F1:68:0B, Freq 2452 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    Yippy:           Infra, 00:23:69:F9:6C:66, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA
    Kareem:          Infra, 00:1C:DF:F5:D6:AF, Freq 2437 MHz, Rate 54 Mb/s, Strength 58 WPA WPA2
    asimpleday:      Infra, 00:22:2D:39:91:76, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA2
    Nirbans:         Infra, 30:46:9A:62:84:18, Freq 2442 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    CMOORE:          Infra, 00:13:F7:AE:5B:EA, Freq 2462 MHz, Rate 54 Mb/s, Strength 58 WPA
    D3GN_SSID0:      Infra, 78:CD:8E:7B:34:79, Freq 2427 MHz, Rate 54 Mb/s, Strength 84 WPA
    allinremi:       Infra, 00:22:2D:74:91:89, Freq 2437 MHz, Rate 54 Mb/s, Strength 94 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:15:C5:64:36:E9

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1  [Auto eth1] ----------------------------------------------------
  Type:              Wired
  Driver:            asix
  State:             connected
  Default:           yes
  HW Address:        00:90:CC:E7:9D:99

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


```--> Yes, I know, there are a SWARM of wireless networks near me (shouldn't have much to do with it though) I'm trying to connect to SSID: bell960

---

### Post by wildmanne39 on 2011-09-01
Hi, that is what I was thinking too, he can not have the usb or the ethernet plugged in when he tries to connect with the broadcom wireless card.

---

### Post by nm_geo on 2011-09-01
BELL960:         Infra, 3C:EA:4F:30:44:81, Freq 2422 MHz, Rate 54 Mb/s, Strength 95 WEP
that one right?  Try to boot without the USB adapter installed too
WEP gives me headaches :D

---

### Post by aoeuis on 2011-09-01
I'm not sure exactly what you mean, but I tried connecting to wireless without having ethernet adapter connected, although I think that may be part of the problem. Thanks a lot so far, I'll retire for the night.

---

### Post by aoeuis on 2011-09-01
> **nm_geo said:**
> BELL960:         Infra, 3C:EA:4F:30:44:81, Freq 2422 MHz, Rate 54 Mb/s, Strength 95 WEP
that one right?  Try to boot without the USB adapter installed too
WEP gives me headaches :D

"without the USB adapter Installed" as in not plugged in, or to uninstall it?
I'll try again tomorrow, there are 6 different types of encryption in wireless security -> security

---

### Post by nm_geo on 2011-09-01
> **aoeuis said:**
> I'm not sure exactly what you mean, but I tried connecting to wireless without having ethernet adapter connected, although I think that may be part of the problem. Thanks a lot so far, I'll retire for the night.

Yes exactly .. The Network manager does not like more than one AP ethernet or wireless connected at one time.. So yes try a boot without the adapter plugged in ..
Then make sure all the wireless entries are correct including the WEP key..

That is why I said WEP gives me headaches.  More aspirin please ;)

---

### Post by aoeuis on 2011-09-02
> **nm_geo said:**
> Yes exactly .. The Network manager does not like more than one AP ethernet or wireless connected at one time.. So yes try a boot without the adapter plugged in ..
Then make sure all the wireless entries are correct including the WEP key..

That is why I said WEP gives me headaches.  More aspirin please ;)

Here's the "PCI sysfs" I got after rebooting without the adapter connected:

```

PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:dfdfc000-dfdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:64:36:e9
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:df9fe000-df9fffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:ce:8f:99:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg

```You probably realized that I'm relatively new to Ubuntu, so here's some information that may help...
-> under the wireless section of network-connections, I made a new entry: Wireless connection 1
  -> last used: never
 -> mode: infrastructure, MTU: auto, available to all users
 -> IPV4 setting: auto DHCP, others blank, checked require IPV4 addressing for this connection to complete
 -> IPV6 method is ignore, and also checked require IPV6 addressing for this connection to complete

Since the "key" below the SSID on my modem is 26 digits long, it should be a WEP 40/128-bit key (hex/ascii) (correct me if that's wrong)
WEP index is default, and authentication is shared key.

--------------------
I made the keyring password equivalent to my sudo password.
I'm not sure about nm-applet configuration, I haven't accessed it.
--------------------
hardware: the internal wireless-broadcom-device should be working, as dual-boot WinXp connects automatically,
-> the internal wired-internet-port might have some problem as it doesn't work in either Ubuntu or Xp
--------------------
maybe some of the above helped?
:)

---

### Post by wildmanne39 on 2011-09-02
Hi, please post the results of these commands:
```
cat /etc/modprobe.d/blacklist.conf
```
```
lsmod | grep b43
```
```
dmesg | grep b43
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
Thank you

---

### Post by aoeuis on 2011-09-03
cat /etc/modprobe.d/blacklist.conf
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



# ugly and loud noise, getting on everyone's nerves; this should be done by a

# nice pulseaudio bing (Ubuntu: #77010)

blacklist pcspkr



# EDAC driver for amd76x clashes with the agp driver preventing the aperture

# from being initialised (Ubuntu: #297750). Blacklist so that the driver

# continues to build and is installable for the few cases where its

# really needed.

blacklist amd76x_edac

```lsmod | grep b43
```

b43                   296610  0 

mac80211              257001  1 b43

cfg80211              156212  2 b43,mac80211

ssb                    45942  2 b43,b44

```dmesg | grep b43
```

[    1.508981] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17

[    1.508996] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64

[   36.110227] b43-phy0: Broadcom 4311 WLAN found (core revision 10)

[   36.285829] Registered led device: b43-phy0::tx

[   36.285935] Registered led device: b43-phy0::rx

[   36.286040] Registered led device: b43-phy0::radio

[   37.540057] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```dmesg | grep wlan0
```

[   37.632623] ADDRCONF(NETDEV_UP): wlan0: link is not ready

[   40.664412] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[   40.871635] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[   41.068047] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[   41.268052] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[   51.976592] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[   52.176240] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[   52.376121] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[   52.576045] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[   63.284590] wlan0: direct probe to 3c:ea:4f:30:44:81 (try 1/3)

[   63.286198] wlan0: direct probe responded

[   63.286217] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[   63.484125] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[   63.684040] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[   63.884048] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[   74.596709] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[   74.796048] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[   74.996048] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[   75.196037] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[   85.920643] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[   86.120057] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[   86.320040] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[   86.520226] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[   97.260122] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[   97.460050] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[   97.660052] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[   97.860046] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  101.356397] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  101.556033] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  101.756047] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  101.956083] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  112.659949] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  112.856054] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  113.056046] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  113.256043] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  123.990447] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  124.188180] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  124.388048] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  124.588246] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  135.315830] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  135.512046] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  135.712037] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  135.912048] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  146.675539] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  146.872051] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  147.072055] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  147.272044] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  158.000912] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  158.200265] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  158.400055] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  158.600040] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  161.364558] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  161.564069] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  161.764048] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  161.964045] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  172.705630] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  172.904052] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  173.104039] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  173.304066] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  184.055026] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  184.252184] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  184.452032] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  184.652064] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  195.388556] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  195.589083] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  195.788042] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  195.988080] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  206.727023] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  206.924045] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  207.124035] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  207.324238] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  218.061332] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  218.260039] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  218.460037] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  218.660051] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  221.342915] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  221.540041] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  221.740153] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  221.940049] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  232.672590] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  232.872142] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  233.072040] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  233.272069] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  244.014192] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  244.212142] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  244.412039] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  244.612247] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  255.336510] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  255.536038] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  255.736039] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  255.936077] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

[  266.660615] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)

[  266.860040] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)

[  267.060045] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 3)

[  267.260067] wlan0: authentication with 3c:ea:4f:30:44:81 timed out

```sudo iwlist scan
```

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wlan0     Interface doesn't support scanning : Device or resource busy

```


--> dmesg | grep wlan0 results don't look right

---

### Post by wildmanne39 on 2011-09-03
Hi, you are correct it is having trouble connecting to the wep. I recommend setting it to just wpa2 and not wep or mixed mode.

If that does not work disable security altogether and see if you can connect then.
Thank you

---

### Post by aoeuis on 2011-09-03
> **wildmanne39 said:**
> 
If that does not work disable security altogether and see if you can connect then.
Thank you
 
Could you elaborate on disabling security? (the steps involved)

---

### Post by wildmanne39 on 2011-09-03
Hi, enter this in your web browser 192.168.0.1 and it should take you to your router setup and under wireless disable or change security to wpa2.

You will need to be hard wired to your router.
Thank you

---

### Post by aoeuis on 2011-09-03
Hurrah, it works now!
Wireless connection is established, but the most confunding aspect of it is that I didn't really change anything... Just tweeked some security settings, reverted them, and rebooted (hmm). 

```

[   37.403033] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.081315] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)
[   46.082878] wlan0: authenticated
[   46.083323] wlan0: associate with 3c:ea:4f:30:44:81 (try 1)
[   46.084781] wlan0: RX AssocResp from 3c:ea:4f:30:44:81 (capab=0x431 status=0 aid=1)
[   46.084787] wlan0: associated
[   46.085831] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   57.016064] wlan0: no IPv6 routers present
[   99.704281] wlan0: deauthenticating from 3c:ea:4f:30:44:81 by local choice (reason=3)
[  101.044581] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)
[  101.244036] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)
[  101.248669] wlan0: authenticated
[  101.249086] wlan0: associate with 3c:ea:4f:30:44:81 (try 1)
[  101.251401] wlan0: RX AssocResp from 3c:ea:4f:30:44:81 (capab=0x431 status=0 aid=1)
[  101.251407] wlan0: associated

```Thank you, wildmanne39 and nm-geo for your patient help! :)
Just one more question, which settings do I need to activate so that upon reboot, the wireless security password is submitted automatically?
Edit: Do I need to configure firmware after updating to 11.11 when released?

---

### Post by wildmanne39 on 2011-09-03
If you have it set to auto connect in network manager and you entered your router password once then it should do it every time.

Please post the results of these commands they might tell us what is going on with encryption.
```
nm-tool
```
```
sudo iwlist scan
```
Thank you

---

### Post by nm_geo on 2011-09-03
Good job guys.. Sorry I was at my mom's house fixing her DSL and other stuff.  Please do the commands wildmanne asked for they will help others too.  Did you get it working with WPA2?

---

### Post by nm_geo on 2011-09-03
> **aoeuis said:**
> Hurrah, it works now!
Wireless connection is established, but the most confunding aspect of it is that I didn't really change anything... Just tweeked some security settings, reverted them, and rebooted (hmm). 

```

[   37.403033] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.081315] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)
[   46.082878] wlan0: authenticated
[   46.083323] wlan0: associate with 3c:ea:4f:30:44:81 (try 1)
[   46.084781] wlan0: RX AssocResp from 3c:ea:4f:30:44:81 (capab=0x431 status=0 aid=1)
[   46.084787] wlan0: associated
[   46.085831] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   57.016064] wlan0: no IPv6 routers present
[   99.704281] wlan0: deauthenticating from 3c:ea:4f:30:44:81 by local choice (reason=3)
[  101.044581] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 1)
[  101.244036] wlan0: authenticate with 3c:ea:4f:30:44:81 (try 2)
[  101.248669] wlan0: authenticated
[  101.249086] wlan0: associate with 3c:ea:4f:30:44:81 (try 1)
[  101.251401] wlan0: RX AssocResp from 3c:ea:4f:30:44:81 (capab=0x431 status=0 aid=1)
[  101.251407] wlan0: associated

```Thank you, wildmanne39 and nm-geo for your patient help! :)
Just one more question, which settings do I need to activate so that upon reboot, the wireless security password is submitted automatically?
Edit: Do I need to configure firmware after updating to 11.11 when released?

You will need to add the passphrase to the network manager wireless page then on reboot all is well.

To answer your other question I am also testing Oneiric using the exact same driver and security as Natty.. No Problem

---

### Post by aoeuis on 2011-09-04
nm tool
```

NetworkManager Tool

State: connected

- Device: wlan0  [Auto BELL960] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        00:16:CE:8F:99:E5

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BELL700:         Infra, 00:25:3C:F3:61:09, Freq 2422 MHz, Rate 54 Mb/s, Strength 60 WEP
    Wlan:            Infra, 00:22:2D:E3:B2:FB, Freq 2457 MHz, Rate 54 Mb/s, Strength 45 WPA
    TRENDnet652:     Infra, 00:14:D1:4E:8A:5B, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA
    tkpk:            Infra, 00:22:2D:A1:0A:61, Freq 2417 MHz, Rate 54 Mb/s, Strength 70 WPA
    SSID:wirelesssm35: Infra, 00:18:D1:64:7A:8B, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WEP
    myLGNet:         Infra, 00:01:36:33:E6:DE, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WEP
    BELL291:         Infra, 00:1B:5B:D5:9F:09, Freq 2447 MHz, Rate 54 Mb/s, Strength 50 WEP
    BELL130:         Infra, 3C:EA:4F:0A:48:39, Freq 2442 MHz, Rate 54 Mb/s, Strength 67 WEP
    Hunter:          Infra, 00:22:2D:68:04:99, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA
    Zebenzki:        Infra, B8:C7:5D:02:A9:A9, Freq 2427 MHz, Rate 54 Mb/s, Strength 50 WPA2
    TK:              Infra, 00:25:9C:F1:68:0B, Freq 2452 MHz, Rate 54 Mb/s, Strength 52 WPA WPA2
    Angelique:       Infra, 00:26:F3:A1:B4:D1, Freq 2457 MHz, Rate 54 Mb/s, Strength 54 WPA
    CTS:             Infra, 00:25:86:B9:D2:30, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA
    *BELL960:        Infra, 3C:EA:4F:30:44:81, Freq 2422 MHz, Rate 54 Mb/s, Strength 95 WEP
    BB:              Infra, 00:26:50:2A:07:D9, Freq 2462 MHz, Rate 54 Mb/s, Strength 57 WEP
    BELL - 611:      Infra, B0:E7:54:65:65:A1, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WEP
    BELL835:         Infra, 3C:EA:4F:9D:7A:49, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WEP
    Siva:            Infra, 00:1B:5B:8C:6C:D1, Freq 2457 MHz, Rate 54 Mb/s, Strength 57 WEP
    BELL550:         Infra, 64:0F:28:34:70:09, Freq 2427 MHz, Rate 54 Mb/s, Strength 45 WEP
    BELL670:         Infra, 00:26:50:41:28:69, Freq 2452 MHz, Rate 54 Mb/s, Strength 57 WEP
    Xuan:            Infra, 00:24:01:77:09:A5, Freq 2437 MHz, Rate 54 Mb/s, Strength 61 WEP
    807:             Infra, 00:22:2D:1D:10:19, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WEP
    Michelle H:      Infra, 00:23:51:AA:CE:91, Freq 2447 MHz, Rate 54 Mb/s, Strength 77 WEP
    BELL729:         Infra, 3C:EA:4F:1D:75:51, Freq 2432 MHz, Rate 54 Mb/s, Strength 92 WEP
    CcNet:           Infra, 00:22:2D:16:40:78, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA
    Sirous:          Infra, 00:24:8C:61:3E:EE, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA
    Gong:            Infra, 00:22:2D:6C:50:D1, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA
    chocolate:       Infra, 70:71:BC:CF:F8:54, Freq 2462 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2
    asimpleday:      Infra, 00:22:2D:39:91:76, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2
    CMOORE:          Infra, 00:13:F7:AE:5B:EA, Freq 2462 MHz, Rate 54 Mb/s, Strength 78 WPA
    Kinley :         Infra, 00:22:15:A8:70:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA
    GJY:             Infra, 00:22:2D:6C:68:31, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA
    BELLinternet:    Infra, C0:83:0A:D8:61:79, Freq 2417 MHz, Rate 54 Mb/s, Strength 57 WPA
    Kareem:          Infra, 00:1C:DF:F5:D6:AF, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    allinremi:       Infra, 00:22:2D:74:91:89, Freq 2437 MHz, Rate 54 Mb/s, Strength 74 WPA
    Yippy:           Infra, 00:23:69:F9:6C:66, Freq 2462 MHz, Rate 54 Mb/s, Strength 85 WPA
    D3GN_SSID0:      Infra, 78:CD:8E:7B:34:79, Freq 2427 MHz, Rate 54 Mb/s, Strength 92 WPA

  IPv4 Settings:
    Address:         192.168.2.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:15:C5:64:36:E9

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


```iwlist scan (terminal doesn't display all of it)
```

                    ESSID:"tkpk"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000326b210148
                    Extra: Last beacon: 1060ms ago
                    IE: Unknown: 0004746B706B
                    IE: Unknown: 010802040B161224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010037127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402050700000000000000000000000000000000000000
          Cell 10 - Address: 00:22:2D:74:91:89
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"allinremi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002f0cec205
                    Extra: Last beacon: 300ms ago
                    IE: Unknown: 0009616C6C696E72656D69
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: 00:23:69:F9:6C:66
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Yippy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000012c92f919a
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 00055969707079
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001300000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B00010310470010AFF7792733BAE1F16B61B803A0533136102100074C696E6B737973102300075752543331304E102400063132333435361042000234321054000800060050F2040001101100075752543331304E100800020084
                    IE: Unknown: DD090010180200F4050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001300000000000000000000000000000000000000
          Cell 12 - Address: 30:46:9A:62:84:18
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Nirbans"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001520dcb6e2
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 00074E697262616E73
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030107
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1607081500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7C0050F204104A00011010440001021041000100103B000103104700107E4D22A0E2FDB95101C5DDCBC94F80351021000D4E4554474541522C20496E632E10230009574E5232303030763210240009574E523230303076321042000230311054000800060050F204000110110009574E52323030307632100800020084
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3407081500000000000000000000000000000000000000
          Cell 13 - Address: 00:24:56:BC:FF:21
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"PJSFinancial"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001b9db3d9181
                    Extra: Last beacon: 1180ms ago
                    IE: Unknown: 000C504A5346696E616E6369616C
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 14 - Address: 00:26:F3:0D:D0:63
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"MLGB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000312447f41b7
                    Extra: Last beacon: 1104ms ago
                    IE: Unknown: 00044D4C4742
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050C000200000000000000000000
                    IE: Unknown: 2A0103
                    IE: Unknown: 32088C129824B048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: 3A:60:77:07:C6:92
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"BrownOak-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b1c674552
                    Extra: Last beacon: 1084ms ago
                    IE: Unknown: 000E42726F776E4F616B2D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 16 - Address: 90:E6:BA:7D:43:FE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"WLAN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000046a3d347005
                    Extra: Last beacon: 1084ms ago
                    IE: Unknown: 0004574C414E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 051300010000010400802018000000000000000008
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180206F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 17 - Address: 3C:EA:4F:9D:7A:49
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"BELL835"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000016b8145
                    Extra: Last beacon: 1068ms ago
                    IE: Unknown: 000742454C4C383335
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 18 - Address: 00:14:D1:4E:8A:5B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"TRENDnet652"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001cd7b6460d7
                    Extra: Last beacon: 1056ms ago
                    IE: Unknown: 000B5452454E446E6574363532
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0C101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C330C101EFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020120
          Cell 19 - Address: C0:83:0A:D8:61:79
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"BELLinternet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c17e79b0ef
                    Extra: Last beacon: 928ms ago
                    IE: Unknown: 000C42454C4C696E7465726E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030102
                    IE: Unknown: 0706555320010B1B
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 20 - Address: 3C:EA:4F:D9:B7:C9
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"BELL623"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005ab5b2b181
                    Extra: Last beacon: 1028ms ago
                    IE: Unknown: 000742454C4C363233
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
          Cell 21 - Address: 74:EA:3A:AD:17:DC
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Martin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013f76a42a8
                    Extra: Last beacon: 984ms ago
                    IE: Unknown: 00064D617274696E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1602081100000000000000000000000000000000000000
                    IE: Unknown: DD730050F204104A00011010440001021041000100103B000103104700102606C2115E5978F17B858ED9F341C62B1021000754502D4C494E4B1023000754502D4C494E4B1024000631323334353610420004313233341054000800060050F20400011011000954442D57383936304E100800020088
                    IE: Unknown: DD090010180200F4050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402081100000000000000000000000000000000000000
          Cell 22 - Address: 00:25:9C:F1:68:0B
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"TK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000355180e
                    Extra: Last beacon: 144ms ago
                    IE: Unknown: 0002544B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD930050F204104A00011010440001021041000100103B000103104700100000000000000001100000259CF1680B102100134C696E6B73797320436F72706F726174696F6E102300075752543132304E1024000776312E302E30341042000C4A555430304B3230303934331054000800060050F204000110110014576972656C65737320526F757465722857464129100800020084
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000
          Cell 23 - Address: B0:E7:54:2A:71:71
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"HOME WIRELESS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005108e2af29
                    Extra: Last beacon: 72ms ago
                    IE: Unknown: 000D484F4D4520574952454C455353
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
          Cell 24 - Address: 00:22:2D:6C:68:31
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"GJY"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000252d8fff14c
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0003474A59
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503005A127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 25 - Address: 00:22:2D:6C:68:32
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000252d8fffaed
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0503005A127A
                    IE: Unknown: DD1E00904C336E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 26 - Address: 00:24:8C:61:3E:EE
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"Sirous"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000047f8b9f17f
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 00065369726F7573
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 27 - Address: 00:22:2D:39:91:76
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"asimpleday"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000075681cc4a6
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000A6173696D706C65646179
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
          Cell 28 - Address: 00:13:F7:AE:5B:EA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"CMOORE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000036a053a8b
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 0006434D4F4F5245
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0102
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


```Hope this helps.
Concerning WPA2: I'm not sure, I haven't changed the settings concerning it.

---

### Post by wildmanne39 on 2011-09-04
Hi, what is the name of the network you are connecting too.
Thank you

---

### Post by aoeuis on 2011-09-04
SSID: Bell 960

---

### Post by wildmanne39 on 2011-09-04
Hi, you are correct your encryption is set back to wep, if you have anymore trouble I would change it to wpa2 plus wpa2 is a lot more secure them wep.
Thank you

---

### Post by aoeuis on 2011-09-05
I see, I'll consider it in the future.
Thanks again for your help -- I learned a bit more about wireless networks in the process.:KS

---

### Post by wildmanne39 on 2011-09-05
Hi, glad I could help if you do not mind would you click on membership application in my signature if you support me for ubuntu membership and leave a recommendation?
Thank you

---

