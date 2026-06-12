---
title: "Linksys WMP11 v2.7 / Broadcom BCM4303 Issue"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by ooboontwo on 2012-06-12
Hey everyone,

I am running 10.10 (Maverick Meerkat) on a *new* build that I put together from old spare parts. I have a very old PCI Wireless Networking Card (Linksys WMP11 v2.7) that I cannot get to work. (Everything else works great! Yay!)

Here's the relevant information:

lspci

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
01:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)

```This is my card: **01:06.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)**

iwconfig
```
lo        no wireless extensions.

eth1      no wireless extensions.

```ifconfig
```
eth1      Link encap:Ethernet  HWaddr 00:19:21:d7:b5:b8  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fed7:b5b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1287150 (1.2 MB)  TX bytes:171361 (171.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```**Strange inconsistencies...**

- When I first loaded up my fresh install of Maverick I saw a proprietary driver available for b43 something in the Additional Drivers Manager. It is now gone for some reason.

- ndis populates the wlan0 field, and allows Network Manager to see and attempt a connection with a network. However, the connection never succeeds, whether the network is secured or unsecured.

**Things I have tried...**

- Lots of googling, including this guide: [http://lkubuntu.wordpress.com/2011/09/08/how-to-fix-broadcom-43xx/](http://lkubuntu.wordpress.com/2011/09/08/how-to-fix-broadcom-43xx/) and also this guide: [URL="http://ubuntuforums.org/showthread.php?t=185174"]http://ubuntuforums.org/showthread.php?t=185174
[/URL] 
- Using wicd instead of Network Manager

- Using ndiswrapper

- b43legacy, b43lpphy, etc. I have purged, reinstalled, rebooted a bajillion times.

- I have moved the card to another physical PCI slot.

- I have all the latest updates for Ubuntu 10.10 (Maverick)

- There is no switch or anything on the card itself. It is always on, and this is not a laptop, it is a hodge-podged-built-from-scraps desktop.

At this point, Network Manager does not even show wireless anything. I am connected through an ethernet port at the moment.

I know that I can fix this problem by purchasing another (more out-of-the-box supported) usb dongle, or wireless PCI card, but I am trying to work with what I've got right now.

Suggestions?

Cheers,
Cody

---

### Post by chili555 on 2012-06-12
> - Using wicd instead of Network Manager

- Using ndiswrapper

- b43legacy, b43lpphy, etc. I have purged, reinstalled, rebooted a bajillion times.

- I have moved the card to another physical PCI slot.

- I have all the latest updates for Ubuntu 10.10 (Maverick)

- There is no switch or anything on the card itself. It is always on, and this is not a laptop, it is a hodge-podged-built-from-scraps desktop.

At this point, Network Manager does not even show wireless anything. I am connected through an ethernet port at the moment.
Oh, my oh my!

Please run and post:```
lspci -nn | grep 0280
lsmod | grep -e wl -e ndis -e b43
ndiswrapper -l
```I have a bet going on with the guys in the back room that I can fix this in eight posts total.

---

### Post by ooboontwo on 2012-06-12
I hope you win your bet!

```
bedroom@bedroom:~$ lspci -nn | grep 0280
01:06.0 Network controller [0280]: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [14e4:4301] (rev 02)
bedroom@bedroom:~$ lsmod | grep -e wl -e ndis -e b43
ndiswrapper           184207  0 
bedroom@bedroom:~$ ndiswrapper -l
bedroom@bedroom:~$ 

```

Cheers,
Cody

---

### Post by chili555 on 2012-06-12
> Broadcom Corporation BCM4303 802.11b Wireless LAN Controller [[COLOR="Red"]14e4:4301[/COLOR]]The accepted best way to get this going is b43legacy, but it needs firmware. Let's see if you have it:```
ls /lib/firmware/b43legacy
```If it's not found, let's get it. With the ethernet cable attached, please do:```
sudo apt-get install b43-fwcutter
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta-3.130.20.0.o
sudo modprobe -r ndiswrapper
sudo modprobe b43legacy
```If it works, we'll need to take a couple of extra steps to make it persistent.

---

### Post by ooboontwo on 2012-06-14
b43legacy is installed

```
bedroom@bedroom:~$ sudo ls /lib/firmware/b43legacy
[sudo] password for bedroom: 
a0g0bsinitvals2.fw  a0g1bsinitvals5.fw    b0g0initvals2.fw  ucode11.fw
a0g0bsinitvals5.fw  a0g1initvals5.fw    b0g0initvals5.fw  ucode2.fw
a0g0initvals2.fw    b0g0bsinitvals2.fw    pcm4.fw          ucode4.fw
a0g0initvals5.fw    b0g0bsinitvals5.fw    pcm5.fw          ucode5.fw
bedroom@bedroom:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  debhelper module-assistant intltool-debian po-debconf libmail-sendmail-perl
  gettext libunistring0 html2text libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bedroom@bedroom:~$ 

```I went ahead and ran the rest of the terminal commands you posted and the additional drivers manager popped up and asked me if I wanted to activate b43legacy.

```
bedroom@bedroom:~$ export FIRMWARE_INSTALL_DIR="/lib/firmware"
bedroom@bedroom:~$ wget http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
--2012-06-14 01:12:18--  http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
Resolving downloads.openwrt.org... 78.24.191.177
Connecting to downloads.openwrt.org|78.24.191.177|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652866 (638K) [text/plain]
Saving to: `wl_apsta-3.130.20.0.o.2'

100%[======================================>] 652,866      317K/s   in 2.0s    

2012-06-14 01:12:20 (317 KB/s) - `wl_apsta-3.130.20.0.o.2' saved [652866/652866]

bedroom@bedroom:~$ sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta-3.130.20.0.o
[sudo] password for bedroom: 
Sorry, try again.
[sudo] password for bedroom: 
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
bedroom@bedroom:~$ sudo modprobe -r ndiswrapper
bedroom@bedroom:~$ sudo modprobe b43legacy
bedroom@bedroom:~$ 

```

I clicked on activate, but it failed, telling me to look at the jockey log file. Here is *what I think* are the relevant details from the log file:

```
2012-06-14 00:36:26,330 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac>
2012-06-14 00:36:26,374 DEBUG: reading modalias file /lib/modules/2.6.35-32-generic/modules.alias
2012-06-14 00:36:26,623 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2012-06-14 00:36:26,629 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2012-06-14 00:36:26,636 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2012-06-14 00:36:26,695 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2012-06-14 00:36:26,711 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2012-06-14 00:36:26,728 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2012-06-14 00:36:26,739 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2012-06-14 00:36:26,745 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2012-06-14 00:36:27,097 DEBUG: loading custom handler /usr/share/jockey/handlers/madwifi.py
2012-06-14 00:36:27,177 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci

2012-06-14 00:36:27,177 DEBUG: Instantiated Handler subclass __builtin__.MadwifiHandler from name MadwifiHandler
2012-06-14 00:36:27,177 DEBUG: Alternate Atheros "madwifi" driver availability undetermined, adding to pool
2012-06-14 00:36:27,177 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2012-06-14 00:36:27,295 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

2012-06-14 00:36:27,297 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver96 from name NvidiaDriver96
2012-06-14 00:36:27,335 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-14 00:36:27,344 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriverCurrent from name NvidiaDriverCurrent
2012-06-14 00:36:27,363 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-14 00:36:27,363 DEBUG: Could not instantiate Handler subclass __builtin__.NvidiaDriverBase from name NvidiaDriverBase
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 914, in get_handlers
    inst = obj(backend)
TypeError: __init__() takes exactly 3 arguments (2 given)
2012-06-14 00:36:27,390 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173

2012-06-14 00:36:27,392 DEBUG: Instantiated Handler subclass __builtin__.NvidiaDriver173 from name NvidiaDriver173
2012-06-14 00:36:27,411 DEBUG: NVIDIA accelerated graphics driver availability undetermined, adding to pool
2012-06-14 00:36:27,411 DEBUG: loading custom handler /usr/share/jockey/handlers/sl_modem.py
2012-06-14 00:36:27,451 DEBUG: Instantiated Handler subclass __builtin__.SlModem from name SlModem
2012-06-14 00:36:27,527 DEBUG: Software modem not available
2012-06-14 00:36:27,528 DEBUG: loading custom handler /usr/share/jockey/handlers/dvb_usb_firmware.py
2012-06-14 00:36:27,629 DEBUG: Instantiated Handler subclass __builtin__.DvbUsbFirmwareHandler from name DvbUsbFirmwareHandler
2012-06-14 00:36:27,630 DEBUG: Firmware for DVB cards not available
2012-06-14 00:36:27,631 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2012-06-14 00:36:27,737 DEBUG: Instantiated Handler subclass __builtin__.BroadcomWLHandler from name BroadcomWLHandler
2012-06-14 00:36:27,738 DEBUG: Broadcom STA wireless driver availability undetermined, adding to pool
2012-06-14 00:36:27,738 DEBUG: loading custom handler /usr/share/jockey/handlers/b43.py
2012-06-14 00:36:27,781 DEBUG: Instantiated Handler subclass __builtin__.B43LegacyHandler from name B43LegacyHandler
2012-06-14 00:36:27,782 DEBUG: Broadcom B43legacy wireless driver availability undetermined, adding to pool
2012-06-14 00:36:27,859 DEBUG: Instantiated Handler subclass __builtin__.B43Handler from name B43Handler
2012-06-14 00:36:27,859 DEBUG: Broadcom B43 wireless driver availability undetermined, adding to pool
2012-06-14 00:36:27,860 DEBUG: loading custom handler /usr/share/jockey/handlers/fglrx.py
2012-06-14 00:36:27,887 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx

2012-06-14 00:36:27,889 DEBUG: Instantiated Handler subclass __builtin__.FglrxDriver from name FglrxDriver
2012-06-14 00:36:27,908 DEBUG: ATI/AMD proprietary FGLRX graphics driver availability undetermined, adding to pool
2012-06-14 00:36:27,908 DEBUG: all custom handlers loaded
2012-06-14 00:36:27,908 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd000003EBsv00001019sd00002601bc0Csc05i00')
2012-06-14 00:36:28,862 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'i2c_nforce2', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:28,863 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2012-06-14 00:36:28,909 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd00000614sv0000196Esd00000719bc03sc00i00')
2012-06-14 00:36:28,924 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nvidiafb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:28,924 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'nouveau', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:28,927 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-06-14 00:36:29,713 DEBUG: got handler xorg:nvidia_current([NvidiaDriverCurrent, nonfree, enabled] NVIDIA accelerated graphics driver)
2012-06-14 00:36:29,740 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-14 00:36:29,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-14 00:36:29,741 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd000003F5sv00001019sd00002601bc05sc00i00')
2012-06-14 00:36:29,756 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'platform:eisa')
2012-06-14 00:36:29,757 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-06-14 00:36:29,820 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2012-06-14 00:36:29,821 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-06-14 00:36:29,835 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:29,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-14 00:36:29,835 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2012-06-14 00:36:29,837 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'k8temp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:29,837 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'platform:regulatory')
2012-06-14 00:36:29,838 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000014E4d00004301sv00001737sd00004301bc02sc80i00')
2012-06-14 00:36:29,926 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ssb', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:29,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-14 00:36:29,927 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000011ABd00004353sv00001019sd00008039bc02sc00i00')
2012-06-14 00:36:29,956 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sky2', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:29,956 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd000003EAsv00001019sd00002601bc05sc00i00')
2012-06-14 00:36:29,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-06-14 00:36:29,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:device:')
2012-06-14 00:36:29,962 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd000003E0sv00001019sd00002601bc06sc01i00')
2012-06-14 00:36:29,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-14 00:36:29,967 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0F13:')
2012-06-14 00:36:29,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-14 00:36:29,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0501:')
2012-06-14 00:36:29,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-06-14 00:36:29,968 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd000003F6sv00001019sd00002601bc01sc01i85')
2012-06-14 00:36:29,973 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'sata_nv', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:29,973 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'ssb:v4243id0807rev01')
2012-06-14 00:36:29,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-14 00:36:29,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-06-14 00:36:29,977 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr6.00PG:bd02/15/2007:svnGateway:pnGT5432:pvr310:rvnELITEGROUP:rnMCP61PM-AM:rvr1.0:cvnGateway:ct3:cvrMCP61PM-AM:')
2012-06-14 00:36:29,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-14 00:36:29,992 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'ssb:v4243id0806rev02')
2012-06-14 00:36:29,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'b44', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:29,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-06-14 00:36:29,993 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'option', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:29,993 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2012-06-14 00:36:29,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0400:')
2012-06-14 00:36:29,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-14 00:36:29,994 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd000003ECsv00001019sd00002601bc01sc01i8a')
2012-06-14 00:36:29,999 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pata_amd', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,000 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd000003F2sv00001019sd00002601bc0Csc03i20')
2012-06-14 00:36:30,005 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd000003F0sv00001019sd0000A88Dbc04sc03i00')
2012-06-14 00:36:30,010 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_hda_intel', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,011 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2012-06-14 00:36:30,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'input:b0011v0002p0001e0001-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-06-14 00:36:30,016 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-14 00:36:30,016 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v000011C1d00000620sv000011C1sd00000621bc07sc80i00')
2012-06-14 00:36:30,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'platform:pcspkr')
2012-06-14 00:36:30,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'pcspkr', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,018 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'snd_pcsp', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,018 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-14 00:36:30,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'serio_raw', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,028 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'psmouse', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,028 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'ssb:v4243id0812rev02')
2012-06-14 00:36:30,029 DEBUG: got handler firmware:b43legacy([B43LegacyHandler, free, disabled] Broadcom B43legacy wireless driver)
2012-06-14 00:36:30,029 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001019sd00008024bc0Csc00i10')
2012-06-14 00:36:30,044 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'ohci1394', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,044 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'firewire_ohci', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,044 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-14 00:36:30,044 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8f060ac> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd000003EBsv00001019sd00002601bc0Csc05i00')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v00001022d00001100sv00000000sd00000000bc06sc00i00')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd00000614sv0000196Esd00000719bc03sc00i00')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0000:')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0200:')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd000003F5sv00001019sd00002601bc05sc00i00')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'platform:eisa')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8E,8F,9B,9C,9D,9E,9F,A3,A4,A5,A6,AC,AD,B7,B8,B9,D9,E2,ram4,l0,1,2,sfw')
2012-06-14 00:36:30,045 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0103:')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'platform:regulatory')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000014E4d00004301sv00001737sd00004301bc02sc80i00')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000011ABd00004353sv00001019sd00008039bc02sc00i00')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd000003EAsv00001019sd00002601bc05sc00i00')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:LNXSYBUS:')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:device:')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd000003E0sv00001019sd00002601bc06sc01i00')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0B00:')
2012-06-14 00:36:30,046 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0F13:')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0100:')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0501:')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd000003F6sv00001019sd00002601bc01sc01i85')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'ssb:v4243id0807rev01')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0C01:')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'dmi:bvnPhoenixTechnologies,LTD:bvr6.00PG:bd02/15/2007:svnGateway:pnGT5432:pvr310:rvnELITEGROUP:rnMCP61PM-AM:rvr1.0:cvnGateway:ct3:cvrMCP61PM-AM:')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0C04:')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'ssb:v4243id0806rev02')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2012-06-14 00:36:30,047 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v00001022d00001102sv00000000sd00000000bc06sc00i00')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0400:')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd000003ECsv00001019sd00002601bc01sc01i8a')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd000003F2sv00001019sd00002601bc0Csc03i20')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd000003F0sv00001019sd0000A88Dbc04sc03i00')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000010DEd000003F3sv000010DEsd0000CB84bc06sc04i01')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'input:b0011v0002p0001e0001-e0,1,2,k110,111,112,r0,1,amlsfw')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0C02:')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v000011C1d00000620sv000011C1sd00000621bc07sc80i00')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'platform:pcspkr')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2012-06-14 00:36:30,048 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'ssb:v4243id0812rev02')
2012-06-14 00:36:30,049 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'pci:v0000104Cd00008024sv00001019sd00008024bc0Csc00i10')
2012-06-14 00:36:30,049 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2012-06-14 00:36:30,049 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x90a068c> about HardwareID('modalias', 'acpi:PNP0800:')
2012-06-14 00:36:30,651 DEBUG: handler xorg:nvidia_current previously unused
2012-06-14 00:36:30,652 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-14 00:36:31,064 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-14 00:36:31,419 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-14 00:36:45,609 DEBUG: Removing package: bcmwl-kernel-source
2012-06-14 00:36:48,059 DEBUG: remove progress statusChange dpkg-exec 0.000000
2012-06-14 00:36:52,595 DEBUG: remove progress statusChange bcmwl-kernel-source 0.000000
2012-06-14 00:36:52,696 DEBUG: remove progress statusChange bcmwl-kernel-source 33.333300
2012-06-14 00:37:18,097 DEBUG: remove progress statusChange bcmwl-kernel-source 66.666700
2012-06-14 00:37:18,846 DEBUG: remove progress statusChange bcmwl-kernel-source 100.000000
2012-06-14 00:37:19,053 DEBUG: remove progress statusChange initramfs-tools 100.000000
2012-06-14 00:37:31,287 DEBUG: (Reading database ... 149361 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-32-generic

2012-06-14 00:37:31,766 DEBUG: unbind/rebind on driver /sys/module/b43legacy/drivers/ssb:b43legacy: device ssb0:0
2012-06-14 00:37:35,201 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-14 00:37:35,571 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-14 00:37:35,900 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-14 00:37:49,643 DEBUG: unbind/rebind on driver /sys/module/b43legacy/drivers/ssb:b43legacy: device ssb0:0
2012-06-14 00:37:51,751 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-14 00:37:52,114 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-14 00:37:52,446 DEBUG: writing back check cache /var/cache/jockey/check
2012-06-14 00:37:55,794 DEBUG: Shutting down
```Cheers,
Cody

---

### Post by chili555 on 2012-06-14
So did it incorrectly install bcmwl-kernel-source? Let's just shortcut the process of finding out and trying to remove it:```
sudo apt-get remove --purge bcmwl-kernel-source
```Now let's load b43legacy:```
sudo modprobe b43legacy
```Did it create a wireless interface?```
iwconfig
```Can you connect? If not please run and post:```
dmesg | grep b43
```Thanks.

Additional Drivers, also known as jockey, struggles with Broadcom wireless cards; they are tricky and I'm not sure all the rules in jockey are correct.

---

### Post by ooboontwo on 2012-06-14
> **chili555 said:**
> So did it incorrectly install bcmwl-kernel-source? Let's just shortcut the process of finding out and trying to remove it:```
sudo apt-get remove --purge bcmwl-kernel-source
```Now let's load b43legacy:```
sudo modprobe b43legacy
```Did it create a wireless interface?```
iwconfig
```Can you connect? If not please run and post:```
dmesg | grep b43
```Thanks.

Additional Drivers, also known as jockey, struggles with Broadcom wireless cards; they are tricky and I'm not sure all the rules in jockey are correct.

Oh boy, this is a headache. Thanks for sticking with me on this one. I appreciate your help.

Here's my terminal output after doing all of that.

```
bedroom@bedroom:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for bedroom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  debhelper intltool-debian po-debconf libmail-sendmail-perl gettext
  libunistring0 html2text libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 149310 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-32-generic
bedroom@bedroom:~$ sudo modprobe b43legacy
bedroom@bedroom:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
bedroom@bedroom:~$ dmesg | grep b43
[  113.422563] b43-pci-bridge 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[  113.422579] b43-pci-bridge 0000:01:06.0: setting latency timer to 64
[  113.512463] b43legacy-phy0: Broadcom 4301 WLAN found
[  113.533034] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[  113.533060] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[  113.557030] b43legacy-phy0 debug: Radio initialized
[  113.984074] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  114.055997] b43legacy-phy0 debug: Chip initialized
[  114.056480] b43legacy-phy0 debug: 30-bit DMA initialized
[  114.057789] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2B
[  114.057797] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x78
[  114.057803] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x2E
[  114.057809] b43legacy-phy0 warning: LEDs: Unknown behaviour 0x19
[  114.057870] b43legacy-phy0 debug: Wireless interface started
[  114.057907] b43legacy-phy0: Radio hardware status changed to DISABLED
[  114.057916] b43legacy-phy0 debug: Radio initialized
[  114.058904] b43legacy-phy0 debug: Adding Interface type 2
[  114.100048] b43legacy-phy0: Radio turned on by software
[  114.100053] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  114.136055] b43legacy-phy0 debug: Removing Interface type 2
[  114.136098] b43legacy-phy0 debug: Wireless interface stopped
[  114.136180] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  114.136224] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 0/64
[  114.136267] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  114.144037] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  114.152011] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  114.160018] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  114.168012] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  114.176016] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  114.180049] b43legacy-phy0 debug: Radio initialized
[  114.180057] b43legacy-phy0 debug: Radio initialized

```

It sounds like b43legacy thinks I have a hardware switch turned off on this card. However, as I previously mentioned, there is no physical hardware switch on the PCI card. The card is most definitely on, because it has a power LED on the backplate of the card, and it is lit up GREEN.

Network Manager has the option "Enable Wireless" greyed out when I right mouse click the applet, and "Wireless is disabled" appears under "Wireless Networks" when I left mouse click on the applet.

Cheers,
Cody

---

### Post by chili555 on 2012-06-14
Let's have a look at:```
rfkill list all
sudo rfkill unblock all
rfkill list all
```

---

### Post by ooboontwo on 2012-06-14
> **chili555 said:**
> Let's have a look at:```
rfkill list all
sudo rfkill unblock all
rfkill list all
```

```
bedroom@bedroom:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
bedroom@bedroom:~$ sudo rfkill unblock all
[sudo] password for bedroom: 
bedroom@bedroom:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
bedroom@bedroom:~$ 

```

Again, it seems to think there is a hardware block on the card (assuming that is what "hard block" means) but there is not (at least, not to my knowledge...)

---

### Post by chili555 on 2012-06-14
I just saw this: [http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)> So many forums suggested different hacks but not close to the solution so they never got it working perfectly.

To solve this problem,
Simply run the command below:```
sudo rm /dev/rfkill

```
After that, simply reboot your computer:```
sudo shutdown -r now

```

When you reboot the device /dev/rfkill deleted will be re-created automatically
and you should be able to connect back to your network.See if anything changes:```
rfkill list all
```

---

### Post by ooboontwo on 2012-06-14
> **chili555 said:**
> I just saw this: [http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)See if anything changes:```
rfkill list all
```

I ran:

```

sudo rm /dev/rfkill

```

and rebooted.

When the computer restarted I ran:

```

rfkill list all
```

Nothing appeared. So, I reloaded b43legacy:

```

sudo modprobe b43legacy
```

Then I ran:

```
rfkill list all
```

And the same thing as before was listed:

```

bedroom@bedroom:~$ rfkill list all 0: phy0: Wireless LAN     Soft blocked: no     Hard blocked: yes
```

Other thoughts?

---

### Post by ooboontwo on 2012-06-14
Bored.

Took the card out and inspected it closely, searching for any kind of switch. I didn't think there was one... and I was right. There is no hardware switch like laptop wireless cards have.

Switched the card to the other PCI slot (I only have two). Nothing changed. After reloading b43legacy and running "rfkill list all" it still shows the card hard blocked.

Since this is a hobby project I don't mind continuing to pursue a solution... if this were a daily use kind of computer I would have already run out and bought a different (more linux friendly) card!

I still hope to get this card working, though. Let me know what you think I should try next.

Cheers,
Cody

---

### Post by chili555 on 2012-06-14
I've worked on a couple of cases, not necessarily b43legacy, where a hard block was removed by resetting the BIOS to default. Please see attached. In the example, press F9 to reset to defaults and F10 to save and reboot. Your BIOS may be different, so check the menu at the bottom.

I am very low on ideas.

---

### Post by ooboontwo on 2012-06-14
> **chili555 said:**
> I've worked on a couple of cases, not necessarily b43legacy, where a hard block was removed by resetting the BIOS to default. Please see attached. In the example, press F9 to reset to defaults and F10 to save and reboot. Your BIOS may be different, so check the menu at the bottom.

I am very low on ideas.

I looked around in the BIOS and didn't see any setting that might hardblock my card, but I didn't try resetting to defaults yet. I will try that next. If that doesn't work, I will install an old copy of Windows XP that I have on this machine. That way I can verify whether or not the card itself is busted. If that works, my next step will be to install Ubuntu 12.04 Precise Pangolin on the machine, and see if that fixes the issue perhaps.

I will let you know how all of that goes. If you have any other ideas let me know. I am suspecting that the card is bad, but we will know for sure after I get Windows XP up and running. If it works in Windows, then we know it isn't the hardware itself.

Thanks again for all your help.

Cheers,
Cody

---

### Post by ooboontwo on 2012-06-15
_***SOLVED.***_

Not sure how to mark the thread as solved, though. I tried to edit my original post, but I didn't see where I could change the tag.

I installed Windows to verify that the card was sound (hardware-wise). I was able to connect using Windows, so that told me the card was good. Next, I installed 12.04 Precise Pangolin and updated everything through the update manager with my ethernet cable attached. I then rebooted and installed Synaptic (I love Synaptic, don't want to live in Ubuntu without it, personally) and installed b43-fwcutter and firmware-b43legacy-installer through synaptic. After that completed I saw wireless networks and was able to connect to my secured network on the first try.

Everything is now running great! I haven't restarted the machine yet, though. I am hoping this is permanent and not just a fluke!!

Thanks for your help, Chili. I hope this thread helps others in some way. My solution was to upgrade from Maverick Meerkat (10.10) to Precise Pangolin (12.04).

Cheers,
Cody

---

### Post by chili555 on 2012-06-15
Awesome! Great news. Thanks for your persistence and explanation.

---

