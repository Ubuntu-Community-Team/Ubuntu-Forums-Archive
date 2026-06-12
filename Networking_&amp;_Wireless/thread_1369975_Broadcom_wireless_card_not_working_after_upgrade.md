---
title: "Broadcom wireless card not working after upgrade"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by Hansmc on 2010-01-01
Ever since I upgraded to the new Ubuntu, I have been having problem with wireless. In the "Hardware Drivers" I come up with 2 drivers:

1) Boadcom B43 wireless driver
2) Broadcon STA wireless driver 

I activated the first one, but latter noticed that the wireless was not working, so I tried installing the second and it returned this message:

> Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log

So I unactivated the first and then it disappeared leaving me with the second, and its error message.


>      4.1.2. Non-recognized Card

   * Some devices are not recognized by the OS upon insertion. [Needs
     expansion.]
        1. If card doesn't show up immediately try these steps:

Run the following command. /Hopefully you'll get some output about the device./

 sudo pccardctl ident



What should I do now?


The output for "lshw -C network":
```
 *-network UNCLAIMED           description: Network controller
      product: BCM4312 802.11b/g
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:0c:00.0
      version: 01
      width: 64 bits
      clock: 33MHz
      capabilities: pm msi pciexpress cap_list
      configuration: latency=0
      resources: memory:f6cfc000-f6cfffff
 *-network
      description: Ethernet interface
      product: NetLink BCM5906M Fast Ethernet PCI Express
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:09:00.0
      logical name: eth0
      version: 02
      serial: 00:23:ae:04:c7:15
      size: 100MB/s
      capacity: 100MB/s
      width: 64 bits
      clock: 33MHz
      capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=sb v3.04 ip=192.168.0.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
      resources: irq:29 memory:f69f0000-f69fffff
```
t2@t2-laptop ~ $


The last few pages of /var/log/jockey.log.

```
<jockey.detection.LocalKernelModulesDriverDB instance at 0x8b053ec> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd00000286bc0Csc03i00')

2010-01-01 17:41:26,713 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b053ec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')

2010-01-01 17:41:26,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}

2010-01-01 17:41:26,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'joydev', 'jockey_handler': 'KernelModuleHandler'}

2010-01-01 17:41:26,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}

2010-01-01 17:41:26,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b053ec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')

2010-01-01 17:41:26,714 DEBUG: no corresponding handler available for {'driver_type': 'kernel_module', 'kernel_module': 'evbug', 'jockey_handler': 'KernelModuleHandler'}

2010-01-01 17:41:26,714 DEBUG: querying driver db <jockey.detection.LocalKernelModulesDriverDB instance at 0x8b053ec> about HardwareID('modalias', 'acpi:PNP0800:')

2010-01-01 17:41:26,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002A03sv00001028sd00000286bc03sc80i00')

2010-01-01 17:41:26,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')

2010-01-01 17:41:26,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00001180d00000592sv00001028sd00000286bc08sc80i00')

2010-01-01 17:41:26,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00001180d00000822sv00001028sd00000286bc08sc05i01')

2010-01-01 17:41:26,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0C01:')

2010-01-01 17:41:26,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0B00:')

2010-01-01 17:41:26,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002834sv00001028sd00000286bc0Csc03i00')

2010-01-01 17:41:26,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw')

2010-01-01 17:41:26,715 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'platform:dcdbas')

2010-01-01 17:41:26,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'usb:v1D6Bp0001d0206dc09dsc00dp00ic09isc00ip00')

2010-01-01 17:41:26,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00001180d00000852sv00001028sd00000286bc08sc80i00')

2010-01-01 17:41:26,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k94,95,A1,E0,E1,EC,EE,1AF,ramlsfw')

2010-01-01 17:41:26,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0000:')

2010-01-01 17:41:26,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002815sv00001028sd00000286bc06sc01i00')

2010-01-01 17:41:26,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'platform:Fixed MDIO bus')

2010-01-01 17:41:26,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002831sv00001028sd00000286bc0Csc03i00')

2010-01-01 17:41:26,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'platform:regulatory')

2010-01-01 17:41:26,716 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00001180d00000843sv00001028sd00000286bc08sc80i00')

2010-01-01 17:41:26,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002A00sv00001028sd00000286bc06sc00i00')

2010-01-01 17:41:26,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:LNXTHERM:')

2010-01-01 17:41:26,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0200:')

2010-01-01 17:41:26,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002A02sv00001028sd00000286bc03sc00i00')

2010-01-01 17:41:26,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0303:')

2010-01-01 17:41:26,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d0000283Asv00001028sd00000286bc0Csc03i20')

2010-01-01 17:41:26,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0C04:')

2010-01-01 17:41:26,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('printer_deviceid', 'MFG:Generic;MDL:CUPS-PDF Printer;DES:Generic CUPS-PDF Printer;CMD:POSTSCRIPT;')

2010-01-01 17:41:26,717 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0103:PNP0C01:')

2010-01-01 17:41:26,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v000014E4d00004315sv00001028sd0000000Bbc02sc80i00')

2010-01-01 17:41:26,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'eisa:sXO_FFFF')

2010-01-01 17:41:26,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00001180d00000832sv00001028sd00000286bc0Csc00i10')

2010-01-01 17:41:26,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0019v0000p0006e0000-e0,1,kE0,E1,E3,F0,F1,F2,F3,F4,F5,ramlsfw')

2010-01-01 17:41:26,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0001v8384p7616e0001-e0,12,kramls1,2,fw')

2010-01-01 17:41:26,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')

2010-01-01 17:41:26,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d0000284Bsv00001028sd00000286bc04sc03i00')

2010-01-01 17:41:26,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'dmi:bvnDellInc.:bvrA03:bd10/23/2008:svnDellInc.:pnInspiron1318:pvr:rvnDellInc.:rn0C236D:rvr:cvnDellInc.:ct8:cvr:')

2010-01-01 17:41:26,718 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:LNXSYSTM:')

2010-01-01 17:41:26,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')

2010-01-01 17:41:26,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')

2010-01-01 17:41:26,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'usb:v046DpC016d0340dc00dsc00dp00ic03isc01ip02')

2010-01-01 17:41:26,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:LNXVIDEO:')

2010-01-01 17:41:26,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0003v046DpC016e0110-e0,1,2,4,k110,111,112,r0,1,8,am4,lsfw')

2010-01-01 17:41:26,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0F13:')

2010-01-01 17:41:26,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002448sv00000000sd00000000bc06sc04i01')

2010-01-01 17:41:26,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002835sv00001028sd00000286bc0Csc03i00')

2010-01-01 17:41:26,719 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002836sv00001028sd00000286bc0Csc03i20')

2010-01-01 17:41:26,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v000014E4d00001713sv00001028sd00000286bc02sc00i00')

2010-01-01 17:41:26,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'platform:pcspkr')

2010-01-01 17:41:26,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0011v0001p0001eAB41-e0,1,4,11,14,k71,72,73,74,75,76,77,79,7A,7B,7C,7D,7E,7F,80,8C,8D,8E,8F,94,98,9B,9C,9D,9E,9F,A2,A3,A4,A5,A6,AC,AD,B7,B8,B9,BF,C1,CD,D4,D7,D9,E0,E1,E2,E3,EC,EE,ram4,l0,1,2,sfw')

2010-01-01 17:41:26,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0100:')

2010-01-01 17:41:26,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002830sv00001028sd00000286bc0Csc03i00')

2010-01-01 17:41:26,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'platform:eisa')

2010-01-01 17:41:26,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d0000283Esv00001028sd00000286bc0Csc05i00')

2010-01-01 17:41:26,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'serio:ty01pr00id00ex00')

2010-01-01 17:41:26,720 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')

2010-01-01 17:41:26,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'pci:v00008086d00002832sv00001028sd00000286bc0Csc03i00')

2010-01-01 17:41:26,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0011v0002p0007e01B1-e0,1,3,k110,111,112,145,14A,ra0,1,18,1C,mlsfw')

2010-01-01 17:41:26,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')

2010-01-01 17:41:26,721 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x8e8fbec> about HardwareID('modalias', 'acpi:PNP0800:')

2010-01-01 17:41:26,746 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:41:26,823 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:41:26,844 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:41:35,100 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:41:44,009 WARNING: modinfo for module wl failed:

2010-01-01 17:41:44,010 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver

2010-01-01 17:41:44,023 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:43:10,330 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:43:10,344 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:43:10,369 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:43:28,947 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:43:31,032 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:43:38,937 DEBUG: _check_polkit_privilege: sender :1.80 on connection <dbus._dbus.SystemBus (system) at 0x8a9605c> pid 2822 is not authorized for com.ubuntu.devicedriver.install: dbus.Dictionary({}, signature=dbus.Signature('ss'))

2010-01-01 17:43:41,727 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:43:59,977 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:44:05,980 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:44:45,710 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:44:46,398 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:44:47,996 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled

2010-01-01 17:45:03,091 WARNING: modinfo for module wl failed:

2010-01-01 17:45:03,092 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver

2010-01-01 17:45:03,112 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: enabled
```

Thanks for your help.

---

### Post by bkratz on 2010-01-01
See this thread it seems to work for a lot of people

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Jcarr_toonist on 2010-01-07
For people still experiencing this issue. I got it working by going into synaptic and removing the bcmwl-kernel driver there(apt-get wouldn't remove it for some reason). Then I tried again in the 'hardware drivers' dialog and it downloaded and installed it correctly.  

After rebooting it worked but I still had issues with it working with my wpa2 secured connection. I got that working using this thread as a guide. 

[http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)

One of the more annoying issues that I have experienced with ubuntu. And for some reason I keep getting broadcom wireless cards. Why? I don't know...

---

### Post by Ostrava on 2010-01-13
> **Jcarr_toonist said:**
> For people still experiencing this issue. I got it working by going into synaptic and removing the bcmwl-kernel driver there(apt-get wouldn't remove it for some reason). Then I tried again in the 'hardware drivers' dialog and it downloaded and installed it correctly.  

After rebooting it worked but I still had issues with it working with my wpa2 secured connection. I got that working using this thread as a guide. 

[http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)

One of the more annoying issues that I have experienced with ubuntu. And for some reason I keep getting broadcom wireless cards. Why? I don't know...

I followed your advice but rather completely uninstalled the bcmwl-kernel then reinstalled it and everything worked and with my wpa2 connection. Thanks for the help.

---

### Post by leorolla on 2010-01-14
Mine is also 4312.

The first linked thread doesn't work for us, it doesn't include 4312.

I tried Jcarr and Ostrava's solutions and neither worked for me.

---

### Post by leorolla on 2010-01-15
Any suggestions?

---

### Post by leorolla on 2010-01-15
After so many hours, I solved the problem with ndiswrapper.

It is fast, stable and hopefully won't be discontinued that soon as seem to be the case with ubuntu hardware driver installer.

---

### Post by itismike on 2010-01-31
> **Jcarr_toonist said:**
> For people still experiencing this issue. I got it working by going into synaptic and removing the bcmwl-kernel driver there(apt-get wouldn't remove it for some reason). Then I tried again in the 'hardware drivers' dialog and it downloaded and installed it correctly...

Same solution worked for me, but I had to activate the Broadcom B43 wireless driver instead.  Tagged the bug with it: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/511379)

---

### Post by TravisLow on 2010-07-17
Not being the "early-adopter" type, I waited until now to upgrade to 10.04 and I ran into the "wireless stopped working" problem on my HP ProBook 4510s.  

I followed the lead of ostrava and jcarr above, and opened the Synaptics Package manager and uninstalled, then reinstalled the Broadcom STA packages.  (bcmwl or some such, I think the name was)

That didn't *quite* do it for me.  I followed the directions here:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

In particular, since the wired network was fine, I rebooted, then toggled my wireless hardware button.  After that, I was able to view the network and then connect to it again.  

Many thanks to everyone who contributed to solving this problem.

---

### Post by abramdemski on 2010-10-27
I have an HP Touchsmart tx2. I never had this problem with 10.4, but I just installed 10.10 and now have exactly the same problem as the original poster (except that the Broadcom STA wireless driver was the only wireless driver in the list of additional drivers, so I didn't try a different driver first).

I tried completely removing and then re-installing bcmwl-kernel using synaptics. This changed the error message from the "check log" message to "SystemError: installArchives() failed" (appearing in a pop-up after I click "activate driver").

Any thoughts appreciated; I'll post if I solve it.

---

### Post by abramdemski on 2010-10-27
PS:

The last few lines of /var/log/Jockey.log *after* I went through everything I described:

2010-10-27 17:52:16,859 DEBUG: BroadcomWLHandler enabled(): kmod enabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-27 17:52:17,027 DEBUG: Removing package: bcmwl-kernel-source
2010-10-27 17:52:17,652 DEBUG: remove progress statusChange dpkg-exec 0.000000

---

### Post by abramdemski on 2010-10-27
It works now! I'm not sure exactly what did it; I went through the same actions again, and also closed the laptop at some point, which would suspend it I guess, not sure of that would make any difference especially since I had already restarted during the process last time... This time I did not restart, by the way; it just worked right away.

---

### Post by kenwag on 2012-04-27
I've just upgraded from Ubuntu 11.10 to 12.4, and the same problem has occurred.
Working WiFi is now not working.

Haven't come very far Ubuntu, have we.

---

### Post by jromer on 2012-04-27
Same issue here. (WIFI not working) Reverted to backup of prior 12.04 beta2 prior to last update. Will wait for fix. I'm not going to tinker around...I expect it to work via the upgrade.

---

### Post by sffvba[e0rt on 2012-04-27
> **kenwag said:**
> I've just upgraded from Ubuntu 11.10 to 12.4, and the same problem has occurred.
Working WiFi is now not working.

Haven't come very far Ubuntu, have we.

> **jromer said:**
> Same issue here. (WIFI not working) Reverted to backup of prior 12.04 beta2 prior to last update. Will wait for fix. I'm not going to tinker around...I expect it to work via the upgrade.

May I suggest starting new threads and giving as much relevant information as possible.

*Old Thread **Closed**.*


404

---

