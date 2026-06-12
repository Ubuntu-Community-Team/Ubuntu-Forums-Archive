---
title: "zoom 4410b usb wireless problem"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by pedrok1664 on 2012-05-12
Hi

I realise that there is a thread about this and i am working my way through it, however i'll let you know where I'm at. First up is some screen outputs

root@peter-T8200:/home/peter# ndiswrapper -l
[B]WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'Desktop'
WARNING: /etc/modprobe.d/blacklist line 2: ignoring bad line starting with 'Documents'
WARNING: /etc/modprobe.d/blacklist line 3: ignoring bad line starting with 'Downloads'
WARNING: /etc/modprobe.d/blacklist line 4: ignoring bad line starting with 'Music'
WARNING: /etc/modprobe.d/blacklist line 5: ignoring bad line starting with 'Pictures'
WARNING: /etc/modprobe.d/blacklist line 6: ignoring bad line starting with 'Public'
WARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with 'Templates'
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'Videos'[/B]
wlanuzg : driver installed
    device (0803:4410) present
root@peter-T8200:/home/peter# lshw -c network
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:08:d3:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.6 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:f7df7000-f7df7fff ioport:dec0(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:23:9d:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=[SIZE=3]**orinoco_cs**[/SIZE] driverversion=3.2.0-24-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b
root@peter-T8200:/home/peter# ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: /etc/modprobe.d/blacklist line 1: ignoring bad line starting with 'Desktop'
WARNING: /etc/modprobe.d/blacklist line 2: ignoring bad line starting with 'Documents'
WARNING: /etc/modprobe.d/blacklist line 3: ignoring bad line starting with 'Downloads'
WARNING: /etc/modprobe.d/blacklist line 4: ignoring bad line starting with 'Music'
WARNING: /etc/modprobe.d/blacklist line 5: ignoring bad line starting with 'Pictures'
WARNING: /etc/modprobe.d/blacklist line 6: ignoring bad line starting with 'Public'
WARNING: /etc/modprobe.d/blacklist line 7: ignoring bad line starting with 'Templates'
WARNING: /etc/modprobe.d/blacklist line 8: ignoring bad line starting with 'Videos'
wlanuzg : driver installed
    device (0803:4410) present
root@peter-T8200:/home/peter# sudo gedit /etc/modprobe.d/blacklist.conf
root@peter-T8200:/home/peter# iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


Where it says driver=orinco_cs should this not be wlanuzg?. Im at the third stage of the thread about ndiswrapper and have already tried blacklisting orinco_cs, however that just made the system not detect wireless at all. Also when i deleted the blacklist i put in for orinoco_cs i got the errors which i have highlighted at the top of the page.

I'm Brand new to Linux so any help would be appreciated

---

### Post by chili555 on 2012-05-12
Man, oh man! I lost the coin toss. Here we go!

You have a little mess on your hands, don't you? Let's take some vital signs first before we plan a strategy. Please plug in the Zoom and run and post:```
lspci -nn | grep 0280
lsusb
```Let's check one issue right away:```
cat /etc/modprobe.d/blacklist
```We'll work out what the blacklist should be and put the correct wording in blacklist.*conf*. Also, please post:```
cat /etc/modprobe.d/blacklist.conf
```> Im at the third stage of the thread about ndiswrapperMay we see a link?

---

### Post by pedrok1664 on 2012-05-12
root@peter-T8200:/home/peter# lspci -nn | grep 0280
root@peter-T8200:/home/peter# lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0803:4410 Zoom Telephonics, Inc. 
root@peter-T8200:/home/peter# cat /etc/modprobe.d/blacklist
Desktop
Documents
Downloads
Music
Pictures
Public
Templates
Videos
root@peter-T8200:/home/peter# cat /etc/modprobe.d/blacklist.conf
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


thanks for helping

---

### Post by chili555 on 2012-05-12
> root@peter-T8200:/home/peter# cat /etc/modprobe.d/blacklist
[COLOR="Red"]Desktop
Documents
Downloads
Music
Pictures
Public
Templates
Videos[/COLOR]I assume these are just words and not folders. Check:```
ls /etc/modprobe.d/blacklist/Desktop
```If they are folders, you should see a list of items within. If it is simply the word 'Desktop' you will see:```
/etc/modprobe.d/blacklist/Desktop
```In other words, a repeat of the word. If that's the case, we can eliminate the entire file:```
sudo rm /etc/modprobe.d/blacklist
```***If in doubt, stop and ask.***

The driver orinoco_cs is not correct for your device: 0803:4410 Zoom Telephonics, Inc. Yet some device has grabbed it and created a wireless interface eth1:> *-network
description: Wireless interface
physical id: 2
logical name: [COLOR="Red"]eth1[/COLOR]
serial: 00:02:2d:23:9d:39
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=[COLOR="Red"]orinoco_cs[/COLOR] driverversion=3.2.0-24-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11bDo you have some other internal or external wireless device? ?? ???

---

### Post by pedrok1664 on 2012-05-12
Right iv removed those "words"

ot@peter-T8200:/# ndiswrapper -l
wlanuzg : driver installed
	device (0803:4410) present


Yes I do have a wired connection 

root@peter-T8200:/# lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.4 USB controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/XP (rev 63)
02:07.0 Multimedia audio controller: Yamaha Corporation YMF-754 [DS-1E Audio Controller]
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:0c.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
02:0d.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
02:0d.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 31)
root@peter-T8200:/#

---

### Post by chili555 on 2012-05-12
I still don't understand. orinoco_cs is actually a driver for a PCMCIA device, not a USB device. If you pull out the Zoom USB and run:```
sudo lshw -C network
```Does orinoco_cs still appear? What does this tell us?```
sudo lspcmcia -v
```> Im at the third stage of the thread about ndiswrapperMay we see the link?

---

### Post by pedrok1664 on 2012-05-12
root@peter-T8200:/# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:00:39:08:d3:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.6 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:f7df7000-f7df7fff ioport:dec0(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:23:9d:39
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=3.2.0-24-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

root@peter-T8200:/# sudo lspcmcia -v
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:0c.0)
    Configuration:    state: on    ready: yes

            Voltage: 3.3V
 Vcc: 3.3V
 Vpp: 0.0V

Socket 0 Device 0:    [orinoco_cs]        (bus ID: 0.0)
    Configuration:    state: on
            [io  0xd100-0xd13f flags 0x108]
            [io  0x0000 flags 0x100]
            [mem 0x00000000 flags 0x200]
            [mem 0x00000000 flags 0x200]
            [mem 0x00000000 flags 0x200]
            [mem 0x00000000 flags 0x200]
            
    Product Name:   TOSHIBA
 Wireless LAN Card
 Version 01.01
 
    Identification:    manf_id: 0x0156    card_id: 0x0002
            function: 6 (network)
            prod_id(1): "TOSHIBA
" (0x1d03483e)
            prod_id(2): "Wireless LAN Card
" (0x6460fbbc)
            prod_id(3): "Version 01.01
" (0x1d656d8f)
            prod_id(4): --- (---)
Socket 1 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:0d.0)
    Configuration:    state: on    ready: yes

Socket 2 Bridge:       [yenta_cardbus]     (bus ID: 0000:02:0d.1)
    Configuration:    state: on    ready: yes

---

### Post by chili555 on 2012-05-12
> Product Name: [COLOR="Red"]TOSHIBA
Wireless LAN Card[/COLOR]
Version 01.01

Identification: manf_id: 0x[COLOR="Red"]0156[/COLOR] card_id: 0x[COLOR="Red"]0002[/COLOR]
function: 6 (network)
prod_id(1): "TOSHIBA
" (0x1d03483e)
prod_id(2): "Wireless LAN Card
" (0x6460fbbc)So, yes, you *do* have a Toshiba wireless PCMCIA card. Usually, PCMCIA cards are sticking right out of a slot on the side of the computer. Is that the case? Can you just remove it?

Did you get the USB Zoom because the Toshiba doesn't work very well? Doesn't do WPA2 encryption or what?

I will check in again tomorrow. Good night.

---

### Post by pedrok1664 on 2012-05-12
No, there is a slot for a pcmcia card but theres nothing in it. I got the Zoom USB because as you'v guessed it dosent support wpa2. Its an old laptop, i just bought it to learn about linux

strange

---

### Post by chili555 on 2012-05-13
Please insert the Zoom USB.

We need to get the internal card out of the way by blacklisting its driver. Please open a terminal and do:```
sudo su
echo "blacklist orinoco_cs" >> /etc/modprobe.d/blacklist.conf
modprobe ndiswrapper
exit
```Now let's see if there are any kernel messages about ndiswrapper:```
dmesg | grep ndis
```> Im at the third stage of the thread about ndiswrapper May we see the link?

Any errors or warnings are important clues, please note and post them.

---

### Post by pedrok1664 on 2012-05-13
Hi chilli,

Right thats me done that, 

I got an error running modprobe ndiswrapper

Heres the output

root@peter-T8200:/home/peter# echo "blacklist orinoco_cs" >> /etc/modprobe.d/blacklist.conf
root@peter-T8200:/home/peter# modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.con, it will be ignored in a future release.
root@peter-T8200:/home/peter# exit
exit
peter@peter-T8200:~$ dmesg | grep ndis
[ 3655.475742] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[ 3655.599423] usbcore: registered new interface driver ndiswrapper
peter@peter-T8200:~$

---

### Post by chili555 on 2012-05-13
It looks like there is a typing error. May I see:```
cat /etc/modprobe.d/blacklist.con
```We'll need to fix up the error.> Im at the third stage of the thread about ndiswrapper May we see the link?

---

### Post by pedrok1664 on 2012-05-13
sorry yeh think it was typo

Blacklist orinoco_cs

That was all that was in it so i removed it and ran nsdiswrapper again. Error free

root@peter-T8200:/etc/modprobe.d# modprobe ndiswrapper
root@peter-T8200:/etc/modprobe.d# exit
exit
peter@peter-T8200:~$ dmesg | grep ndis
[ 3655.475742] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[ 3655.599423] usbcore: registered new interface driver ndiswrapper
peter@peter-T8200:~$

---

### Post by chili555 on 2012-05-13
Now how about:```
ndiswrapper -l
iwconfig
```Thanks.

If I could get the link you referred to, I'd like to look at the .inf file. How about it?

---

### Post by pedrok1664 on 2012-05-13
root@peter-T8200:/home/peter# ndiswrapper -l
wlanuzg : driver installed
root@peter-T8200:/home/peter# iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

still showing as eth1

---

### Post by chili555 on 2012-05-13
Did you reboot after you blacklisted orinoco_cs? Let's see:```
cat /etc/modprobe.d/blacklist.conf
```You only need post the last 5 lines.> root@peter-T8200:/home/peter# ndiswrapper -l
wlanuzg : driver installed
[COLOR="Red"]but no device present[/COLOR]After you reboot, plug in the device and try again:```
ndiswrapper -l
```

Once again, if I could get the link you referred to, I'd like to look at the .inf file. How about it?

---

### Post by pedrok1664 on 2012-05-13
peter@peter-T8200:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0803:4410 Zoom Telephonics, Inc. 
peter@peter-T8200:~$ ndiswrapper -l
wlanuzg : driver installed
    device (0803:4410) present
peter@peter-T8200:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

peter@peter-T8200:~$ 

 
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
**blacklist orinoco_cs**

Ok thats rebooted, not detecting any wireless now

---

### Post by chili555 on 2012-05-13
Once again, if I could get the link you referred to, I'd like to look at the .inf file. How about it?

Please post:```
dmesg | grep ndis
```Once again, if I could get the link you referred to, I'd like to look at the .inf file. How about it?

Please.> blacklist orinoco_csPerfect!

---

### Post by pedrok1664 on 2012-05-13
eter@peter-T8200:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

#

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist orinoco_cs

peter@peter-T8200:~$ dmesg | grep ndis
peter@peter-T8200:~$

---

### Post by pedrok1664 on 2012-05-13
Sorry, was it the zoom driver .inf

This is it 



peter@peter-T8200:/usr/src/ndiswrapper_1.57/Driver$ cat WlanUZG.inf
;***********************************************************************
; WlanUZG.INF
;
;   This installation script supports Windows 98SE, ME, 2000, XP for the
;   Wireless LAN Adapters.
;
;   Copyright (c) 2007 Zoom Technologies, Inc
;   All Rights Reserved.
;
;***********************************************************************

[Version]
DriverVer        = 08/08/2007,1.7.1.4
Signature        = "$Chicago$"
Compatible        = 1
Class            = Net
ClassGUID        = {4d36e972-e325-11ce-bfc1-08002be10318}
MillenniumPreferred    = .ME
Provider        = %DRV_PROVIDER_STR%
CatalogFile.NT        = WlanUZG.cat


[Manufacturer]
%MANUFACTURER_STR%    = DeviceList, NTx86.5.1, NTAMD64.5.1

;[ControlFlags]
;Exclude all PNP adapters from user selection
;ExcludeFromSelect   = *


[DeviceList]
;DisplayName              Section           Hardware ID
;-----------              -------           --------------------------
%WLAN_XG762N_DESC_STR%             = WLAN_USB1,         USB\Vid_0803&Pid_4410

[DeviceList.NTx86.5.1]
%WLAN_XG762N_DESC_STR%           = WLAN_USB1.XP,        USB\Vid_0803&Pid_4410

[DeviceList.NTAMD64.5.1]
%WLAN_XG762N_DESC_STR%           = WLAN_USB1.NTAMD64,     USB\Vid_0803&Pid_4410

;######################################################################
;   Microsoft Windows 98 section
;######################################################################
[WLAN_USB1]
AddReg        = WLAN_USB1.reg, WLAN_USB_9X_COMMON, WLAN_USB_Common.reg
CopyFiles       = WLAN_USB_DRIVER_COPY_9X

[WLAN_USB1.reg]
HKR,NDI,              DeviceID,           0, "USB\Vid_0803&Pid_4410"
HKR,,                 VendorDesc,         0, %WLAN_XG762N_DESC_STR%

;######################################################################
;   Microsoft Windows Me section
;######################################################################
[WLAN_USB1.ME]
Characteristics = 0x84
BusType         = 15
AddReg        = WLAN_USB1_ME, WLAN_USB_Me.reg, WLAN_USB_Common.reg
CopyFiles       = WLAN_USB_DRIVER_COPY_ME

[WLAN_USB1_ME]
HKR,,                 VendorDesc,         0, %WLAN_XG762N_DESC_STR%

[WLAN_USB1.ME.Services]
AddService = "XG762NME", 2, WLAN_USB_ME.Service, WLAN_USB.EventLog

;========================================================================
[WLAN_USB_Me.reg]
HKR,NDI,              Service,            0, "XG762NME"
HKR,,                 DevLoader,          0, "*ndis"
HKR,,                 DeviceVxDs,         0, "WlanUZME.sys"
HKR,,                 EnumPropPages,      0, "netdi.dll,EnumPropPages"

; NDIS Info
HKR,NDIS,             MajorNdisVersion,   1, 05
HKR,NDIS,             MinorNdisVersion,   1, 00
HKR,NDIS,             LogDriverName,      0, "WLANUZME"

; Interfaces Info
HKR,NDI\Interfaces,   DefUpper,           0, "ndis5"
HKR,NDI\Interfaces,   DefLower,           0, "ethernet"
HKR,NDI\Interfaces,   UpperRange,         0, "ndis5"
HKR,NDI\Interfaces,   LowerRange,         0, "ethernet"

; Install Sections
HKR,NDI\Install,      ndis3,              0, "ZD1211.ndis5me"


[WLAN_USB_ME.Service]
DisplayName     = %WLAN_USB_SERVICE_STR%
ServiceType     = 1                             ; %SERVICE_KERNEL_DRIVER%
StartType       = 3                             ; %SERVICE_DEMAND_START%
ErrorControl    = 1                             ; %SERVICE_ERROR_NORMAL%
ServiceBinary   = %11%\"WlanUZME.sys"        ; %11%\WlanUZME.sys
LoadOrderGroup  = NDIS

;######################################################################
;   Microsoft Windows 2000 section
;######################################################################
[WLAN_USB1.NT]
Characteristics = 0x84
BusType         = 15
AddReg        = WLAN_USB1_2K, WLAN_USB_2K.reg, WLAN_USB_Common.reg
CopyFiles       = WLAN_USB_DRIVER_COPY_2K

[WLAN_USB1_2K]
HKR,,                 VendorDesc,         0, %WLAN_XG762N_DESC_STR%

[WLAN_USB1.NT.Services]
AddService = "XG762N2K", 2, WLAN_USB_2K.Service, WLAN_USB.EventLog
;======================================================================

[WLAN_USB_2K.reg]
; Interfaces Info
HKR,NDI\Interfaces,   UpperRange,         0, "ndis5"
HKR,NDI\Interfaces,   LowerRange,         0, "ethernet"
HKR,NDI,              Service,            0, "XG762N2K"


[WLAN_USB_2K.Service]
DisplayName     = %WLAN_USB_SERVICE_STR%
ServiceType     = 1                             ; %SERVICE_KERNEL_DRIVER%
StartType       = 3                             ; %SERVICE_DEMAND_START%
ErrorControl    = 1                             ; %SERVICE_ERROR_NORMAL%
ServiceBinary   = %12%\WlanUZ2K.sys        ; 
LoadOrderGroup  = NDIS

;######################################################################
;   Microsoft Windows XP section
;######################################################################
[WLAN_USB1.XP.NT]
Characteristics = 0x84
BusType         = 15
AddReg        = WLAN_USB1_XP, WLAN_USB_XP.reg, WLAN_USB_Common.reg
CopyFiles       = WLAN_USB_DRIVER_COPY_XP

[WLAN_USB1_XP]
HKR,,                 VendorDesc,         0, %WLAN_XG762N_DESC_STR%

[WLAN_USB1.XP.NT.Services]
AddService = "XG762NXP", 2, WLAN_USB_XP.Service, WLAN_USB.EventLog

[WLAN_USB_XP.reg]
; Interfaces Info
HKR,NDI\Interfaces,   UpperRange,         0, "ndis5"
HKR,NDI\Interfaces,   LowerRange,         0, "ethernet"
HKR,NDI,              Service,            0, "XG762NXP"
;######################################################################
;   Microsoft Windows XP AMD64 section
;######################################################################
[WLAN_USB1.NTAMD64]
Characteristics = 0x84
BusType         = 15
AddReg        = WLAN_USB1_64,WLAN_USB_64.reg, WLAN_USB_Common.reg
CopyFiles       = WLAN_USB_DRIVER_COPY_XP64

[WLAN_USB1_64]
HKR,,                 VendorDesc,         0, %WLAN_XG762N_DESC_STR%

[WLAN_USB1.NTAMD64.Services]
AddService = "XG762N64", 2, WLAN_USB_NTAMD64.Service, WLAN_USB.EventLog

[WLAN_USB_64.reg]
; Interfaces Info
HKR,NDI\Interfaces,   UpperRange,         0, "ndis5"
HKR,NDI\Interfaces,   LowerRange,         0, "ethernet"
HKR,NDI,              Service,            0, "XG762N64"

;=========================winxp common=======================================


[WLAN_USB_XP.Service]
DisplayName     = %WLAN_USB_SERVICE_STR%
ServiceType     = 1                             ; %SERVICE_KERNEL_DRIVER%
StartType       = 3                             ; %SERVICE_DEMAND_START%
ErrorControl    = 1                             ; %SERVICE_ERROR_NORMAL%
ServiceBinary   = %12%\WlanUZXP.sys        ; 
LoadOrderGroup  = NDIS

[WLAN_USB_NTAMD64.Service]
DisplayName     = %WLAN_USB_SERVICE_STR%
ServiceType     = 1                             ; %SERVICE_KERNEL_DRIVER%
StartType       = 3                             ; %SERVICE_DEMAND_START%
ErrorControl    = 1                             ; %SERVICE_ERROR_NORMAL%
ServiceBinary   = %12%\WlanUZ64.sys        ; 
LoadOrderGroup  = NDIS

;*********************************************************************
;   Microsoft Windows ME/2000/XP Common Section
;*********************************************************************
[WLAN_USB.EventLog]
Addreg = WLAN_USB.AddEventLog.reg

[WLAN_USB.AddEventLog.reg]
HKR,,                               EventMessageFile,  0x00020000, "%%SystemRoot%%\System32\netevent.dll"
HKR,,                               TypesSupported,    0x00010001, 7


;******************************************************************************

[WLAN_USB_9X_COMMON]

 HKR,NDI,              CardType,           0, "PNP"
 HKR,,                 DevLoader,          0, "*ndis"
 HKR,,                 DeviceVxDs,         0, "WlanUZ98.sys"

 ; NDIS Info
 HKR,NDIS,             MajorNdisVersion,   1, 03
 HKR,NDIS,             MinorNdisVersion,   1, 0A
 HKR,NDIS,             LogDriverName,      0, "WLANUZ98"

 ; Interfaces Info
 HKR,NDI\Interfaces,   DefUpper,           0, "ndis3"
 HKR,NDI\Interfaces,   DefLower,           0, "ethernet"
 HKR,NDI\Interfaces,   UpperRange,         0, "ndis3"
 HKR,NDI\Interfaces,   LowerRange,         0, "ethernet"

 ; Other Info
 HKR,,                 BusType,            0, 15
 HKR,,                 IOBaseAddress,      1, 02,00,00,00
 HKR,,                 InterruptNumber,    1, 04,00,00,00
 HKR,,                 EnumPropPages,      0, "netdi.dll,EnumPropPages"

 ; Install Sections
 HKR,NDI\Install,      ndis3,              0, "ZD1211.ndis3"

[WLAN_USB_Common.reg]
HKR, Ndi\params\NumRfd,         ParamDesc,      0, "%ReceiveFrameDescriptors%"
HKR, Ndi\params\NumRfd,         default,        0, "32"
HKR, Ndi\params\NumRfd,         min,            0, "1"
HKR, Ndi\params\NumRfd,         max,            0, "00001024"
HKR, Ndi\params\NumRfd,         step,           0, "1"
HKR, Ndi\params\NumRfd,         Base,           0, "10"
HKR, Ndi\params\NumRfd,         type,           0, "int"
HKR, Ndi\params\NumRfd,         flag,         1, 20,00,00,00

HKR, Ndi\params\NumTcb,         ParamDesc,      0, "%TransmitControlBlocks%"
HKR, Ndi\params\NumTcb,         default,        0, "32"
HKR, Ndi\params\NumTcb,         min,            0, "1"
HKR, Ndi\params\NumTcb,         max,            0, "00000064"
HKR, Ndi\params\NumTcb,         step,           0, "1"
HKR, Ndi\params\NumTcb,         Base,           0, "10"
HKR, Ndi\params\NumTcb,         type,        0, "int"
HKR, Ndi\params\NumTcb,         flag,        1, 20,00,00,00

HKR, Ndi\params\NumCoalesce,    ParamDesc,      0, "%CoalesceBuffers%"
HKR, Ndi\params\NumCoalesce,    default,        0, "128"
HKR, Ndi\params\NumCoalesce,    min,            0, "1"
HKR, Ndi\params\NumCoalesce,    max,            0, "00000128"
HKR, Ndi\params\NumCoalesce,    step,           0, "1"
HKR, Ndi\params\NumCoalesce,    Base,           0, "10"
HKR, Ndi\params\NumCoalesce,    type,           0, "int"
HKR, Ndi\params\NumCoalesce,    flag,         1, 20,00,00,00

HKR,,                               PreambleMode,   0, "0"
HKR,NDI\params\PreambleMode,        ParamDesc,      0, "%PREAMBLE%"
HKR,NDI\params\PreambleMode,           type,           0, "enum"
HKR,NDI\params\PreambleMode,               flag,           1, 30,00,00,00
HKR,Ndi\params\PreambleMode,               default,        0, "3"
HKR,NDI\params\PreambleMode\enum,          1,              0, "Long"
HKR,NDI\params\PreambleMode\enum,          2,              0, "Short"
HKR,NDI\params\PreambleMode\enum,          3,              0, "Auto"

HKR,,                                   IBSS Wireless Mode,   0, "0"
HKR,NDI\params\IBSS Wireless Mode,            ParamDesc,      0, "IBSS Wireless Mode"
HKR,NDI\params\IBSS Wireless Mode,           type,           0, "enum"
HKR,NDI\params\IBSS Wireless Mode,               flag,           1, 30,00,00,00
HKR,Ndi\params\IBSS Wireless Mode,               default,        0, "0"
HKR,NDI\params\IBSS Wireless Mode\enum,          0,              0, "IBSS B Mode"
HKR,NDI\params\IBSS Wireless Mode\enum,          1,              0, "IBSS G Mode"

HKR,,                               IBSS Protection Mode,0, "0"
HKR,NDI\params\IBSS Protection Mode,        ParamDesc,      0, "IBSS Protection Mode"
HKR,NDI\params\IBSS Protection Mode,           type,           0, "enum"
HKR,NDI\params\IBSS Protection Mode,         flag,           1, 30,00,00,00
HKR,Ndi\params\IBSS Protection Mode,         default,        0, "0"
HKR,NDI\params\IBSS Protection Mode\enum,    0,              0, "Disable"
HKR,NDI\params\IBSS Protection Mode\enum,    1,              0, "Enable"

HKR,,                                        Use_G_Mode_in_Usb1.1,0, "0"
HKR,NDI\params\Use_G_Mode_in_Usb1.1,         ParamDesc,      0, "Use_G_Mode_in_Usb1.1"
HKR,NDI\params\Use_G_Mode_in_Usb1.1,             type,           0, "enum"
HKR,NDI\params\Use_G_Mode_in_Usb1.1,             flag,           1, 30,00,00,00
HKR,Ndi\params\Use_G_Mode_in_Usb1.1,             default,        0, "0"
HKR,NDI\params\Use_G_Mode_in_Usb1.1\enum,        0,              0, "Disable"
HKR,NDI\params\Use_G_Mode_in_Usb1.1\enum,        1,              0, "Enable"

HKR,,                               PSPXLinkMode,   0, "0"
HKR,NDI\params\PSPXLinkMode,        ParamDesc,      0, "PSPXLinkMode"
HKR,NDI\params\PSPXLinkMode,           type,           0, "enum"
HKR,NDI\params\PSPXLinkMode,               flag,           1, 30,00,00,00
HKR,Ndi\params\PSPXLinkMode,               default,        0, "0"
HKR,NDI\params\PSPXLinkMode\enum,          0,              0, "Disable"
HKR,NDI\params\PSPXLinkMode\enum,          1,              0, "Enable"

HKR,,                               QosTagPolicy,   0, "0"
HKR,NDI\params\QosTagPolicy,        ParamDesc,      0, "QosTagPolicy"
HKR,NDI\params\QosTagPolicy,           type,           0, "enum"
HKR,NDI\params\QosTagPolicy,               flag,           1, 30,00,00,00
HKR,Ndi\params\QosTagPolicy,               default,        0, "0"
HKR,NDI\params\QosTagPolicy\enum,          0,              0, "Auto"
HKR,NDI\params\QosTagPolicy\enum,          1,              0, "802.1Q Tag"
HKR,NDI\params\QosTagPolicy\enum,          2,              0, "DSCP Tag"

HKR,,                               WMMQosSupport,   0, "0"
HKR,NDI\params\WMMQosSupport,        ParamDesc,      0, "WMMQosSupport"
HKR,NDI\params\WMMQosSupport,           type,           0, "enum"
HKR,NDI\params\WMMQosSupport,              flag,           1, 30,00,00,00
HKR,Ndi\params\WMMQosSupport,           default,        0, "0"
HKR,NDI\params\WMMQosSupport\enum,      0,              0, "Disable"
HKR,NDI\params\WMMQosSupport\enum,      1,              0, "Enable"

HKR,,                               TxBurstingModeSupport,   0, "0"
HKR,NDI\params\TxBurstingModeSupport,        ParamDesc,       0, "TxBurstingModeSupport"
HKR,NDI\params\TxBurstingModeSupport,           type,            0, "enum"
HKR,NDI\params\TxBurstingModeSupport,           flag,            1, 30,00,00,00
HKR,Ndi\params\TxBurstingModeSupport,           default,         0, "0"
HKR,NDI\params\TxBurstingModeSupport\enum,      0,               0, "Disable"
HKR,NDI\params\TxBurstingModeSupport\enum,      1,               0, "Enable"

HKR,,                           PHY_A_6M_Setpoint_Value,    0x10001, 0x28
HKR,,                           PHY_A_6M_CR128_Value,    0x10001, 0x17
HKR,,                           PHY_A_1dBm_Value,    0x10001, 0x08

HKR,,                           EnableAntennaDiversity, 0, "0"
HKR,,                           DefaultAntenna, 0, "0"
HKR,,                           DefaultWirelessMode, 0, "0"

HKR,,                           SaveDefaultConnection, 0, "1"
HKR,,                           RFSwitch, 0, "0"
; FastRoaming: 1000(1sec) <= value <= 4000(4 sec)
HKR,,                           FastRoaming, 0, "4000" 
HKR,,                           EnableFastRoaming, 0, "0" 
HKR,,                           FwRadio, 0, "0" 

;*********************************************************************
;   Destination Directories
;*********************************************************************
[DestinationDirs]
WLAN_USB_DRIVER_COPY_9X        = 11            ; system subdirectory on Win 98
WLAN_USB_DRIVER_COPY_ME        = 11            ; system subdirectory on Win Me
WLAN_USB_DRIVER_COPY_2K        = 12            ; system32\drivers subdirectory on Win NT/2000
WLAN_USB_DRIVER_COPY_XP        = 12            ; system32\drivers subdirectory on Win XP
WLAN_USB_DRIVER_COPY_XP64    = 12            ; system32\drivers subdirectory on Win XP


[PreCopySection]
HKR,,NoSetupUI,,1

[WLAN_USB_DRIVER_COPY_9X]
WlanUZ98.sys

[WLAN_USB_DRIVER_COPY_ME]
WlanUZME.sys

[WLAN_USB_DRIVER_COPY_2K]
WlanUZ2K.sys

[WLAN_USB_DRIVER_COPY_XP]
WlanUZXP.sys

[WLAN_USB_DRIVER_COPY_XP64]
WlanUZ64.sys

[SourceDisksNames]
;Source Disk ID         = Disk Name
;--------------           ---------
 1                      = %INSTALL_DISK_STR%,,,

[SourceDisksFiles]      
;File Name              = Source Disk ID
;---------                --------------
WlanUZ98.sys         = 1
WlanUZ2K.sys             = 1
WlanUZXP.sys         = 1
WlanUZME.sys            = 1
WlanUZ64.sys         = 1

;###############################################################################
[Strings]
DRV_PROVIDER_STR    = "Zoom Technologies, Inc"
MANUFACTURER_STR    = "Zoom Technologies, Inc"

INSTALL_DISK_STR    = "Zoom Wireless-G USB Install Disk"

WLAN_XG762N_DESC_STR    = "Zoom Wireless-G USB adapter"
WLAN_USB_SERVICE_STR     = "Zoom 802.11g XG762 Driver"

PREAMBLE         = "PreambleMode"
CoalesceBuffers     = "CoalesceBuffers"

ReceiveFrameDescriptors = "ReceiveFrameDescriptors"
TransmitControlBlocks   = "TransmitControlBlocks"peter@peter-T8200:/usr/src/ndis

---

### Post by chili555 on 2012-05-13
I'm tired of asking for the link. I'm trying, as hard as I can, to figure out which step or steps you missed or did incorrectly.

---

### Post by pedrok1664 on 2012-05-13
sorry mate,

[http://www.youtube.com/watch?v=v0Ist9aEKEg](http://www.youtube.com/watch?v=v0Ist9aEKEg)

was a tutorial i followed to install the driver

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

I was following this guide to try and fix it

---

### Post by pedrok1664 on 2012-05-13
also just tried 

modprobe ndisswrapper and system just hangs if thats of any help

---

