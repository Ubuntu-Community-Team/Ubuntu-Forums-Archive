---
title: "i recently istalled ubuntu 8.10 but wireless disableed"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by jrranbrody on 2008-12-29
i have recently installed ubuntu 8.10 but when i tried connection to the internet via wireless it wont allow me. i know it is disabled can some one help me enable it? i have a Dell inspiron 1501 AMD 64 Athlon.

---

### Post by pytheas22 on 2008-12-29
Please post the output of these commands:
```

lspci -nn
lsusb
lshw -C Network
sudo iwlist scan
uname -rm
```

And when you say that it won't allow you to connect to your wireless network, what do you mean exactly?  Do you see your wireless network listed but the connection just isn't successful when attempted, or can you not see any wireless networks at all?

---

### Post by 67GTA on 2008-12-29
Your card isn't supported out of the box. There is a step by step tutorial here to get it going with ndiswrapper. It lets you use the Windows driver in Linux. [http://www.ubuntu1501.com/2008/11/ndiswrapper-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntu1501.com/2008/11/ndiswrapper-in-ubuntu-810-intrepid-ibex.html)

---

### Post by jrranbrody on 2008-12-30
[QUOTE=pytheas22;6459867]Please post the output of these commands:
```

lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)

lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1c:26:58:e4:80
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:96:26:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.103 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: a6:ea:a0:af:cb:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

uname -rm
```
it gives me invalid option.
when i try to connect im not able to see any network to connect to

---

### Post by pytheas22 on 2008-12-30
Your wireless card is supposed to be supported in Ubuntu 8.10 by the 'wl' driver, and it is bringing up the device.  But for some reason it looks like it can't scan.

So instead of using 'wl', please try running these commands to get it working via ndiswrapper:
```

sudo apt-get install ndiswrapper-utils-1.9
sudo apt-get install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo modprobe -r wl
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
```

Please post the output of all these commands so I can make sure they run successfully (some of them will have no output).

At this point, you should be able to connect until the next reboot.  If ndiswrapper works, we can make it remain active between reboots.

---

### Post by pytheas22 on 2008-12-30
EDIT: post deleted because it's a duplicate.

---

### Post by jrranbrody on 2008-12-30
thank you for your response. i typed all the commands you gave and they all seem to work. then i rebooted my laptop but still my wireless connection is disabled. hope you can still help me

---

### Post by 67GTA on 2008-12-30
Silly question, but do you have a switch on your laptop that turns wireless on/off?

---

### Post by jrranbrody on 2008-12-30
i dont have a switch to turn on and off the wireless

---

### Post by pytheas22 on 2008-12-31
> i typed all the commands you gave and they all seem to work. then i rebooted my laptop but still my wireless connection is disabled. hope you can still help me

Those commands didn't make any permanent changes--after a reboot, you would default back to your original un-working configuration.

Please run the following commands and post the output here.  They'll let us know whether ndiswrapper is going to work with your card.  If it does, we can install it permanently.  If it doesn't, we'll look at other solutions:
```

ndiswrapper -l
sudo modprobe -r wl ndiswrapper
sudo modprobe ndiswrapper
lshw -C Network
sudo iwlist scan
dmesg | grep -e ndis -e wlan
```

---

### Post by jrranbrody on 2008-12-31
i tried the commands you posted but still nothing happend?
here is what i typed and what it came back. any other suggestion you think we can try?

 ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: wl)
 sudo modprobe -r wl ndiswrapper
 
 sudo modprobe ndiswrapper
lshw -C Nework
WARNING: you should run this program as super-user.
sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

 dmesg | grep -e ndis -e wlan
[   19.084501] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   19.163974] usbcore: registered new interface driver ndiswrapper
[78000.230297] usbcore: deregistering interface driver ndiswrapper
[78022.858078] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[78022.999263] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[78023.005651] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[78023.006642] ndiswrapper 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[78023.006758] ndiswrapper 0000:05:00.0: setting latency timer to 64
[78023.012285] ndiswrapper: using IRQ 18
[78023.216458] wlan0: ethernet device 00:1c:26:58:e4:80 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[78023.216628] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[78023.228344] usbcore: registered new interface driver ndiswrapper
[78027.266273] ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by pytheas22 on 2008-12-31
ndiswrapper is up and running correctly; it just appears that you can't see your network with it.  Is your computer really far from your router?  Is your router in 11g mode or something else?  It may also help to try changing the channel that your router is broadcasting on (6 is usually the best).

The last possibility that I can think of is to use the b43 driver, which should also work with your card.  If you can't get your computer to see your network under ndiswrapper no matter what you do, please post the output of these commands:
```

sudo apt-get update
sudo apt-get install b43-fwcutter
sudo modprobe -r b43 wl ndiswrapper
sudo modprobe b43
iwconfig
sudo iwlist scan
```

---

### Post by jrranbrody on 2009-01-01
sudo apt-get update
[sudo] password
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Reading package lists... Done
 sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.9kB of archives.
After this operation, 106kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main b43-fwcutter 1:011-4ubuntu1 [16.9kB]
Fetched 16.9kB in 45s (369B/s)                         
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 115837 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a011-4ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:011-4ubuntu1) ...
--2009-01-01 16:46:33--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org... 195.56.146.238
Connecting to downloads.openwrt.org|195.56.146.238|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652866 (638K) [application/x-object]
Saving to: `wl_apsta-3.130.20.0.o'

100%[======================================>] 652,866      147K/s   in 4.8s    

2009-01-01 16:46:39 (132 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

--2009-01-01 16:46:39--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Resolving mirror2.openwrt.org... 88.198.39.176
Connecting to mirror2.openwrt.org|88.198.39.176|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3888794 (3.7M) [application/x-tar]
Saving to: `broadcom-wl-4.150.10.5.tar.bz2'

100%[======================================>] 3,888,794    159K/s   in 27s     

2009-01-01 16:47:07 (139 KB/s) - `broadcom-wl-4.150.10.5.tar.bz2' saved [3888794/3888794]

This file is recognised as:
  ID         :  FW10
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw
This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/pcm4.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/ucode4.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/a0g0bsinitvals4.fw
Extracting b43/a0g0initvals4.fw
Extracting b43/b0g0bsinitvals4.fw
Extracting b43/b0g0initvals4.fw
sudo modprobe -r b43 wl ndiswrapper
sudo modprobe b43
 iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

these are the results i got from the codes you gave me and still no wireless connection

---

### Post by pytheas22 on 2009-01-01
It looks like everything is working fine under the new driver; it just can't see your router for some reason.  On a computer that is connected to your router, could you please open a web browser and put 192.168.1.1 in the address bar?  This should bring you to the configuration page for your router (if it asks for a username and password, you can usually find the defaults printed on the outside of the router).

In the configuration page, please verify that your router is operating in 11g mode (if it's in mixed 11b/11g mode, try switching to 11g only), and try switching it to operate on channel 6.  With these changes, can Ubuntu see the router?

---

### Post by jrranbrody on 2009-01-02
i made the changes you suggested and still no wireless connection. im able to connect wireless with other computers but they have windows. any other suggestions?

---

### Post by pytheas22 on 2009-01-02
Could you please post the entire output of the command:
```

dmesg
```

Do you have a switch on this laptop to turn the wireless on and off, or is there a way to turn it on in BIOS?

---

### Post by jrranbrody on 2009-01-07
these is the output of the command you gave me. hope this is helpful for you.
[    0.606765] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.616276] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[    0.616524] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[    0.616769] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[    0.617012] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[    0.617254] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[    0.617496] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[    0.617746] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[    0.617988] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[    0.618232] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[    0.618351] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.618351] pnp: PnP ACPI init
[    0.618351] ACPI: bus type pnp registered
[    0.624078] pnp 00:08: io resource (0x22-0x23) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624083] pnp 00:08: io resource (0x2e-0x2f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624087] pnp 00:08: io resource (0x72-0x73) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624091] pnp 00:08: io resource (0x68-0x6f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624094] pnp 00:08: io resource (0xb0-0xb1) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624098] pnp 00:08: io resource (0x92-0x92) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624102] pnp 00:08: io resource (0x220-0x22f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624106] pnp 00:08: io resource (0x40b-0x40b) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624109] pnp 00:08: io resource (0x4d0-0x4d1) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624113] pnp 00:08: io resource (0x4d6-0x4d6) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624117] pnp 00:08: io resource (0x530-0x537) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624121] pnp 00:08: io resource (0xc00-0xc01) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624124] pnp 00:08: io resource (0xc14-0xc14) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624128] pnp 00:08: io resource (0xc50-0xc52) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624132] pnp 00:08: io resource (0xc6c-0xc6c) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624136] pnp 00:08: io resource (0xc6f-0xc6f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624139] pnp 00:08: io resource (0xcd0-0xcd3) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624143] pnp 00:08: io resource (0xcd4-0xcd5) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624147] pnp 00:08: io resource (0xcd6-0xcd7) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624151] pnp 00:08: io resource (0xcd8-0xcdf) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624155] pnp 00:08: io resource (0xf40-0xf47) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624159] pnp 00:08: io resource (0x87f-0x87f) overlaps 0000:00:05.0 BAR 7 (0x0-0xfff), disabling
[    0.624294] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:05.0 BAR 8 (0x0-0xfffff), disabling
[    0.624298] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:00:05.0 BAR 8 (0x0-0xfffff), disabling
[    0.624323] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[    0.624401] pnp: PnP ACPI: found 10 devices
[    0.624401] ACPI: ACPI bus type pnp unregistered
[    0.624401] PCI: Using ACPI for IRQ routing
[    0.624401] pci 0000:00:05.0: BAR 7: can't allocate resource
[    0.624401] pci 0000:00:05.0: BAR 8: can't allocate resource
[    0.636045] NET: Registered protocol family 8
[    0.636047] NET: Registered protocol family 20
[    0.640043] NetLabel: Initializing
[    0.640043] NetLabel:  domain hash size = 128
[    0.640043] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.640062] NetLabel:  unlabeled traffic allowed by default
[    0.642199] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.642203]    actual entries 65586
[    0.642394] AppArmor: AppArmor Filesystem Enabled
[    0.642425] ACPI: RTC can wake from S4
[    0.652068] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.652073] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.652076] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[    0.652093] system 00:08: ioport range 0x1080-0x1080 has been reserved
[    0.652098] system 00:08: ioport range 0x8000-0x805f has been reserved
[    0.652108] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[    0.652111] system 00:09: iomem range 0xc0004800-0xc0004bff has been reserved
[    0.652115] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.659099] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.659099] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.659099] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff
[    0.659099] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff
[    0.659099] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02
[    0.659099] pci 0000:00:05.0:   IO window: disabled
[    0.659099] pci 0000:00:05.0:   MEM window: disabled
[    0.659099] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.659099] pci 0000:00:06.0: PCI bridge, secondary bus 0000:05
[    0.659099] pci 0000:00:06.0:   IO window: disabled
[    0.659099] pci 0000:00:06.0:   MEM window: 0xc0200000-0xc02fffff
[    0.659099] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.659099] pci 0000:00:14.4: PCI bridge, secondary bus 0000:08
[    0.659099] pci 0000:00:14.4:   IO window: disabled
[    0.659099] pci 0000:00:14.4:   MEM window: 0xc0300000-0xc03fffff
[    0.659099] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.659099] pci 0000:00:05.0: setting latency timer to 64
[    0.659099] pci 0000:00:06.0: setting latency timer to 64
[    0.659099] bus: 00 index 0 io port: [0, ffff]
[    0.659099] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.659099] bus: 01 index 0 io port: [9000, 9fff]
[    0.659099] bus: 01 index 1 mmio: [c0100000, c01fffff]
[    0.659099] bus: 01 index 2 mmio: [c8000000, cfffffff]
[    0.659099] bus: 01 index 3 mmio: [0, 0]
[    0.659099] bus: 02 index 0 mmio: [0, fff]
[    0.659099] bus: 02 index 1 mmio: [0, fffff]
[    0.659099] bus: 02 index 2 mmio: [0, 0]
[    0.659099] bus: 02 index 3 mmio: [0, 0]
[    0.659099] bus: 05 index 0 mmio: [0, 0]
[    0.659099] bus: 05 index 1 mmio: [c0200000, c02fffff]
[    0.659099] bus: 05 index 2 mmio: [0, 0]
[    0.659099] bus: 05 index 3 mmio: [0, 0]
[    0.659099] bus: 08 index 0 mmio: [0, 0]
[    0.659099] bus: 08 index 1 mmio: [c0300000, c03fffff]
[    0.659099] bus: 08 index 2 mmio: [0, 0]
[    0.659099] bus: 08 index 3 io port: [0, ffff]
[    0.659099] bus: 08 index 4 mmio: [0, ffffffffffffffff]
[    0.659099] NET: Registered protocol family 2
[    0.664060] Switched to high resolution mode on CPU 0
[    0.664091] Switched to high resolution mode on CPU 1
[    0.697201] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.698518] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.702687] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.703677] TCP: Hash tables configured (established 262144 bind 65536)
[    0.703681] TCP reno registered
[    0.713170] NET: Registered protocol family 1
[    0.713347] checking if image is initramfs... it is
[    1.718271] Freeing initrd memory: 8450k freed
[    1.728655] audit: initializing netlink socket (disabled)
[    1.728674] type=2000 audit(1231208249.728:1): initialized
[    1.735734] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.740719] VFS: Disk quotas dquot_6.5.1
[    1.740879] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.741082] msgmni has been set to 3762
[    1.741295] io scheduler noop registered
[    1.741298] io scheduler anticipatory registered
[    1.741300] io scheduler deadline registered
[    1.741547] io scheduler cfq registered (default)
[    1.741557] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[    1.741680] pci 0000:01:05.0: Boot video device
[    1.741874] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.741901] pcieport-driver 0000:00:05.0: found MSI capability
[    1.741910] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.742008] pci_express 0000:00:05.0:pcie02: allocate port service
[    1.742132] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.742157] pcieport-driver 0000:00:06.0: found MSI capability
[    1.742161] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.742250] pci_express 0000:00:06.0:pcie02: allocate port service
[    1.811812] Linux agpgart interface v0.103
[    1.811819] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.815837] brd: module loaded
[    1.815963] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.816186] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    1.818774] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.818786] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.841330] mice: PS/2 mouse device common for all mice
[    1.841612] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.841644] rtc0: alarms up to one month
[    1.841729] cpuidle: using governor ladder
[    1.841732] cpuidle: using governor menu
[    1.842200] TCP cubic registered
[    1.842656] registered taskstats version 1
[    1.842860]   Magic number: 9:346:257
[    1.843034] rtc_cmos 00:04: setting system clock to 2009-01-06 02:17:32 UTC (1231208252)
[    1.843038] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.843041] EDD information not available.
[    1.843115] Freeing unused kernel memory: 536k freed
[    1.843544] Write protecting the kernel read-only data: 4348k
[    1.872644] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    2.070589] fuse init (API version 7.9)
[    2.177374] ACPI: processor limited to max C-state 1
[    2.177504] processor ACPI0007:00: registered as cooling_device0
[    2.177509] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.177629] processor ACPI0007:01: registered as cooling_device1
[    2.210970] thermal LNXTHERM:01: registered as thermal_zone0
[    2.213119] ACPI: Thermal Zone [THRM] (31 C)
[    2.649887] No dock devices found.
[    2.685948] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.685961] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
[    2.724559] usbcore: registered new interface driver usbfs
[    2.724595] usbcore: registered new interface driver hub
[    2.725328] usbcore: registered new device driver usb
[    2.753305] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.756173] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0
[    2.756229] SCSI subsystem initialized
[    2.756277] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.756299] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.756374] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[    2.756412] ohci_hcd 0000:00:13.0: irq 16, io mem 0xc0005000
[    2.813333] usb usb1: configuration #1 chosen from 1 choice
[    2.813388] hub 1-0:1.0: USB hub found
[    2.813406] hub 1-0:1.0: 2 ports detected
[    2.872581] libata version 3.00 loaded.
[    3.021427] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.021452] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.021498] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[    3.021537] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0006000
[    3.077303] usb usb2: configuration #1 chosen from 1 choice
[    3.077353] hub 2-0:1.0: USB hub found
[    3.077370] hub 2-0:1.0: 2 ports detected
[    3.157043] usb 1-1: new full speed USB device using ohci_hcd and address 2
[    3.183384] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.183408] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    3.183449] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.183491] ohci_hcd 0000:00:13.2: irq 18, io mem 0xc0007000
[    3.237313] usb usb3: configuration #1 chosen from 1 choice
[    3.237363] hub 3-0:1.0: USB hub found
[    3.237378] hub 3-0:1.0: 2 ports detected
[    3.337574] usb 1-1: configuration #1 chosen from 1 choice
[    3.341289] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.341313] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    3.341354] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[    3.341380] ohci_hcd 0000:00:13.3: irq 17, io mem 0xc0008000
[    3.397297] usb usb4: configuration #1 chosen from 1 choice
[    3.397339] hub 4-0:1.0: USB hub found
[    3.397354] hub 4-0:1.0: 2 ports detected
[    3.501420] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.501444] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    3.501487] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[    3.501514] ohci_hcd 0000:00:13.4: irq 18, io mem 0xc0009000
[    3.557295] usb usb5: configuration #1 chosen from 1 choice
[    3.557335] hub 5-0:1.0: USB hub found
[    3.557350] hub 5-0:1.0: 2 ports detected
[    3.661386] ahci 0000:00:12.0: version 3.0
[    3.661416] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    3.661449] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    3.661564] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    3.661569] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    3.662134] scsi0 : ahci
[    3.662335] scsi1 : ahci
[    3.662453] scsi2 : ahci
[    3.662572] scsi3 : ahci
[    3.662720] ata1: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004100 irq 22
[    3.662725] ata2: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004180 irq 22
[    3.662729] ata3: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004200 irq 22
[    3.662734] ata4: SATA max UDMA/133 abar m1024@0xc0004000 port 0xc0004280 irq 22
[    4.148058] ata1: softreset failed (device not ready)
[    4.148067] ata1: failed due to HW bug, retry pmp=0
[    4.312074] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.312963] ata1.00: ATA-7: ST980811AS, 3.CDD, max UDMA/133
[    4.312968] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.312978] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.314003] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.314007] ata1.00: configured for UDMA/133
[    4.648065] ata2: SATA link down (SStatus 0 SControl 300)
[    4.985081] ata3: SATA link down (SStatus 0 SControl 300)
[    5.320072] ata4: SATA link down (SStatus 0 SControl 300)
[    5.336117] isa bounce pool size: 16 pages
[    5.336237] scsi 0:0:0:0: Direct-Access     ATA      ST980811AS       3.CD PQ: 0 ANSI: 5
[    5.336662] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    5.336682] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    5.336737] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[    5.336791] ehci_hcd 0000:00:13.5: debug port 1
[    5.336821] ehci_hcd 0000:00:13.5: irq 19, io mem 0xc0004400
[    5.349048] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.349259] usb usb6: configuration #1 chosen from 1 choice
[    5.349297] hub 6-0:1.0: USB hub found
[    5.349309] hub 6-0:1.0: 10 ports detected
[    5.361080] usb 1-1: USB disconnect, address 2
[    5.558450] b44 0000:08:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    5.617143] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[    5.622454] b44.c:v2.0
[    5.622717] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.622766] pata_acpi 0000:00:14.1: setting latency timer to 64
[    5.633960] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    5.641586] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:96:26:2e
[    5.650767] scsi4 : pata_atiixp
[    5.650919] scsi5 : pata_atiixp
[    5.652206] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8420 irq 14
[    5.652210] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8428 irq 15
[    5.669067] usb 6-1: new high speed USB device using ehci_hcd and address 2
[    5.675203] Driver 'sd' needs updating - please use bus_type methods
[    5.675380] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.675412] sd 0:0:0:0: [sda] Write Protect is off
[    5.675415] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.675469] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.675595] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    5.675623] sd 0:0:0:0: [sda] Write Protect is off
[    5.675626] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.675678] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.675683]  sda: sda1 sda2 < sda5 >
[    5.722721] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.803095] usb 6-1: configuration #1 chosen from 1 choice
[    5.805142] usbcore: registered new interface driver libusual
[    5.822128] Initializing USB Mass Storage driver...
[    5.823128] scsi6 : SCSI emulation for USB Mass Storage devices
[    5.823344] usbcore: registered new interface driver usb-storage
[    5.823349] USB Mass Storage support registered.
[    5.823674] usb-storage: device found at 2
[    5.823679] usb-storage: waiting for device to settle before scanning
[    5.840579] ata5.00: ATAPI: TSSTcorp DVD+/-RW TS-L632D, DE04, max UDMA/33
[    5.876509] ata5.00: configured for UDMA/33
[    6.041053] scsi 4:0:0:0: CD-ROM            TSSTcorp DVD+-RW TS-L632D DE04 PQ: 0 ANSI: 5
[    6.041299] scsi 4:0:0:0: Attached scsi generic sg1 type 5
[    6.080950] Driver 'sr' needs updating - please use bus_type methods
[    6.144576] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    6.144582] Uniform CD-ROM driver Revision: 3.20
[    6.144735] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    6.364489] PM: Starting manual resume from disk
[    6.364495] PM: Resume from partition 8:5
[    6.364497] PM: Checking hibernation image.
[    6.364840] PM: Resume from disk failed.
[    6.441586] kjournald starting.  Commit interval 5 seconds
[    6.441612] EXT3-fs: mounted filesystem with ordered data mode.
[   10.821449] usb-storage: device scan complete
[   10.822004] scsi 6:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.04 PQ: 0 ANSI: 2
[   10.822489] scsi 6:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  4.04 PQ: 0 ANSI: 2
[   10.823733] sd 6:0:0:0: [sdb] 8013457 512-byte hardware sectors (4103 MB)
[   10.824232] sd 6:0:0:0: [sdb] Write Protect is off
[   10.824235] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.824238] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   10.825856] sd 6:0:0:0: [sdb] 8013457 512-byte hardware sectors (4103 MB)
[   10.826359] sd 6:0:0:0: [sdb] Write Protect is off
[   10.826362] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[   10.826365] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   10.826371]  sdb: sdb1
[   10.827284] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   10.827430] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   10.828363] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[   10.828470] sr 6:0:0:1: Attached scsi CD-ROM sr1
[   10.828569] sr 6:0:0:1: Attached scsi generic sg3 type 5
[   13.912603] udevd version 124 started
[   14.467411] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.521346] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.594352] ACPI: Battery Slot [BAT1] (battery absent)
[   14.595331] ACPI: AC Adapter [ACAD] (on-line)
[   14.652058] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   14.680569] ACPI: Power Button (FF) [PWRF]
[   14.680771] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   14.712070] ACPI: Power Button (CM) [PWRB]
[   14.712318] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   14.744058] ACPI: Sleep Button (CM) [SLPB]
[   14.744203] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[   14.744993] ACPI: Lid Switch [LID]
[   14.746005] ACPI: WMI: Mapper loaded
[   15.162834] ieee80211_crypt: registered algorithm 'NULL'
[   15.168576] acpi device:1e: registered as cooling_device2
[   15.168783] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/device:1c/input/input6
[   15.173014] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.209546] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   15.676279] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8410, revision 0
[   16.085946] sdhci: Secure Digital Host Controller Interface driver
[   16.085951] sdhci: Copyright(c) Pierre Ossman
[   16.176450] sdhci-pci 0000:08:01.0: SDHCI controller found [1180:0822] (rev 19)
[   16.176478] sdhci-pci 0000:08:01.0: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[   16.179586] mmc0: SDHCI controller on PCI [0000:08:01.0] using PIO
[   16.190675] b43-phy0: Broadcom 4311 WLAN found
[   16.264092] ricoh-mmc: Ricoh MMC Controller disabling driver
[   16.264096] ricoh-mmc: Copyright(c) Philip Langdale
[   16.277736] phy0: Selected rate control algorithm 'pid'
[   16.401390] ricoh-mmc: Ricoh MMC controller found at 0000:08:01.1 [1180:0843] (rev 1)
[   16.401410] ricoh-mmc: Main firewire function not found. Cannot disable controller.
[   16.401492] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   16.626930] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.854928] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x180b1, caps: 0xa04713/0x200000
[   16.890022] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   16.951861] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   16.951939] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   18.961735] lp: driver loaded but no devices found
[   19.101051] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   19.181754] usbcore: registered new interface driver ndiswrapper
[   19.462177] Adding 3229024k swap on /dev/sda5.  Priority:-1 extents:1 across:3229024k
[   20.093037] EXT3 FS on sda1, internal journal
[   21.341477] type=1505 audit(1231208271.666:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4289
[   21.561850] type=1505 audit(1231208271.886:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4294
[   21.562151] type=1505 audit(1231208271.886:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4294
[   21.805236] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.038087] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53 processors (2 cpu cores) (version 2.20.00)
[   23.038186] powernow-k8:    0 : fid 0x9 (1700 MHz), vid 0x13
[   23.038191] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x14
[   23.038194] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1a
[   24.041387] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   24.353522] ppdev: user-space parallel port driver
[   26.661028] Clocksource tsc unstable (delta = -160949346 ns)
[   27.038650] Bluetooth: Core ver 2.13
[   27.041912] NET: Registered protocol family 31
[   27.041927] Bluetooth: HCI device and connection manager initialized
[   27.041936] Bluetooth: HCI socket layer initialized
[   27.087096] Bluetooth: L2CAP ver 2.11
[   27.087117] Bluetooth: L2CAP socket layer initialized
[   27.125785] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.125815] Bluetooth: BNEP filters: protocol multicast
[   27.183335] Bridge firewalling registered
[   27.186728] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   27.241102] Bluetooth: SCO (Voice Link) ver 0.6
[   27.241129] Bluetooth: SCO socket layer initialized
[   27.376422] Bluetooth: RFCOMM socket layer initialized
[   27.377236] Bluetooth: RFCOMM TTY layer initialized
[   27.377252] Bluetooth: RFCOMM ver 1.10
[   29.634342] pci 0000:01:05.0: power state changed by ACPI to D0
[   29.634395] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   30.029468] [drm] Initialized drm 1.1.0 20060810
[   30.050867] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   30.559627] [drm] Setting GART location based on new memory map
[   30.562964] [drm] Loading R300 Microcode
[   30.562994] [drm] Num pipes: 4
[   30.563005] [drm] writeback test succeeded in 1 usecs
[   31.706645] input: b43-phy0 as /devices/virtual/input/input9
[   31.812100] firmware: requesting b43/ucode5.fw
[   31.965879] firmware: requesting b43/pcm5.fw
[   31.983926] firmware: requesting b43/b0g0initvals5.fw
[   32.024518] firmware: requesting b43/b0g0bsinitvals5.fw
[   32.152074] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   32.324951] Registered led device: b43-phy0::tx
[   32.331095] Registered led device: b43-phy0::rx
[   32.331837] Registered led device: b43-phy0::radio
[   32.728071] b43-phy0: Radio hardware status changed to DISABLED
[   32.817085] b43-phy0: Radio turned on by software
[   32.817108] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[   34.820228] b44: eth0: Link is up at 100 Mbps, full duplex.
[   34.820244] b44: eth0: Flow control is off for TX and off for RX.
[   35.227479] NET: Registered protocol family 17
[   37.986604] hda-intel: Invalid position buffer, using LPIB read method instead.
[   40.371820] NET: Registered protocol family 10
[   40.376537] lo: Disabled Privacy Extensions
[   40.383510] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.673035] eth0: no IPv6 routers present
[   74.114770] CPU0 attaching NULL sched-domain.
[   74.114814] CPU1 attaching NULL sched-domain.
[   74.125207] CPU0 attaching sched-domain:
[   74.125224]  domain 0: span 0-1 level CPU
[   74.125233]   groups: 0 1
[   74.125245]   domain 1: span 0-1 level NODE
[   74.125251]    groups: 0-1
[   74.125264] CPU1 attaching sched-domain:
[   74.125269]  domain 0: span 0-1 level CPU
[   74.125274]   groups: 1 0
[   74.125283]   domain 1: span 0-1 level NODE
[   74.125289]    groups: 0-1
[  504.736024] APIC error on CPU0: 00(40)
[  504.736039] APIC error on CPU1: 00(40)
[  535.230292] usb 6-1: USB disconnect, address 2
[  727.488034] APIC error on CPU0: 40(40)
[  727.488046] APIC error on CPU1: 40(40)
[ 4848.560662] npviewer.bin[10413]: segfault at ff9d0aa0 ip 00000000ff9d0aa0 sp 00000000ffa3ee7c error 14
[ 5050.433020] APIC error on CPU0: 40(40)
[ 5050.433035] APIC error on CPU1: 40(40)
[ 5182.333023] APIC error on CPU0: 40(40)
[ 5182.333038] APIC error on CPU1: 40(40)
[ 5332.420033] APIC error on CPU1: 40(40)
[ 5332.420046] APIC error on CPU0: 40(40)
[ 6087.130555] APIC error on CPU0: 40(40)
[ 6087.130567] APIC error on CPU1: 40(40)
[ 6993.516027] APIC error on CPU1: 40(40)
[ 6993.516033] APIC error on CPU0: 40(40)
[ 8833.816152] b44: eth0: Link is down.
[150999.461017] APIC error on CPU0: 40(40)
[150999.461030] APIC error on CPU1: 40(40)
[174939.816245] b44: eth0: Link is up at 100 Mbps, full duplex.
[174939.816262] b44: eth0: Flow control is off for TX and off for RX

---

### Post by pytheas22 on 2009-01-07
Thanks for that information.  This is the key to your problem:
```

[ 32.728071] b43-phy0: Radio hardware status changed to DISABLED
[ 32.817085] b43-phy0: Radio turned on by software
[ 32.817108] b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
```

It means that the wireless card is turned off via a switch.  Do you know where that switch is?  Usually it's either a physical button above your keyboard or on the side of your laptop somewhere, or a software switch that you toggle by pressing Function+F2, for example.  Can you flip the switch to turn on the radio, and then wait a few seconds to see if the output of the command 'sudo iwlist scan' detects your wireless network?

If you don't have a switch or it doesn't seem to work, you should also check your BIOS.  Sometimes there's an option to force the wireless radio to be always on.  Other options may include 'always off' or 'application-controlled'.  Try switching it to 'always on'.

---

### Post by jrranbrody on 2009-01-07
thank you very much for all your help i finally able to connect wireless. again thank you for all your help

---

