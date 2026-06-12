---
title: "Can't Get Wireless to Work on Dell Inspiron 1545 with Broadcom BCM4312 [14e4:4315]"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by nicvia on 2010-10-12
I'm a total Ubuntu noob. So I just installed Ubuntu 10.04 LTS Lucid Lynx on my Dell Inspiron 1545 and I can't get the wireless to work. I'm currently on a wired connection. In Hardware Drivers, I was able to install Broadcom B43 wireless driver and it says that it is activated and currently in use. Under that driver is the Broadcom STA wireless driver, which is not activated. Whenever I try to activate it, it ends up saying SystemError: installArchives() failed and when I click an icon in the panel in the top right, it says 'Sorry, the package "bcmwl-kernel-source" failed to install or upgrade'. When I try to connect, it says 'Connection Established' but when I open a browser it can never connect. Any help would be appreciated. Thanks!

---

### Post by nicvia on 2010-10-12
Anyone?

---

### Post by johnnytm on 2010-10-12
I have the same system and noticed the B43 driver does not work. disable it and try to enable the sta broadcomm driver. But even after that I still had to boot twice enabling the wireless each time in order to connect. However an upgrade to 10.10 maverick and using the sta broadcomm driver this problem has disappeared and all works well now

---

### Post by nicvia on 2010-10-13
> **johnnytm said:**
> I have the same system and noticed the B43 driver does not work. disable it and try to enable the sta broadcomm driver. But even after that I still had to boot twice enabling the wireless each time in order to connect. However an upgrade to 10.10 maverick and using the sta broadcomm driver this problem has disappeared and all works well now

Ok, so I updated to 10.10, but whenever I go on 'Additional Drivers' and activate the Broadcom STA wireless driver, it says: "Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

This is what it says in jockey.log:

2010-10-13 21:08:36,554 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'acpi:PNP0100:')
2010-10-13 21:08:36,554 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'input:b0019v0000p0005e0000-e0,5,kramlsfw0,')
2010-10-13 21:08:36,555 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-10-13 21:08:36,555 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'usb:v0BDAp0158d5888dc00dsc00dp00ic08isc06ip50')
2010-10-13 21:08:36,555 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'pci:v00008086d00002929sv00001028sd000002AAbc01sc06i01')
2010-10-13 21:08:36,555 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-10-13 21:08:36,555 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'acpi:PNP0800:')
2010-10-13 21:08:36,555 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'pci:v00008086d0000293Esv00001028sd000002AAbc04sc03i00')
2010-10-13 21:08:36,555 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'wmi:05901221-D566-11D1-B2F0-00A0C9062910')
2010-10-13 21:08:36,555 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'pci:v00008086d00002919sv00001028sd000002AAbc06sc01i00')
2010-10-13 21:08:36,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'pci:v00008086d0000293Csv00001028sd000002AAbc0Csc03i20')
2010-10-13 21:08:36,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'acpi:LNXTHERM:')
2010-10-13 21:08:36,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'platform:pcspkr')
2010-10-13 21:08:36,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'input:b0011v0002p0008e7321-e0,1,3,k110,111,112,145,14A,ra0,1,18,mlsfw')
2010-10-13 21:08:36,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'wmi:8D9DDCBC-A997-11DA-B012-B622A1EF5492')
2010-10-13 21:08:36,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'usb:v05CAp180Ad8730dcEFdsc02dp01ic0Eisc01ip00')
2010-10-13 21:08:36,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'wmi:A80593CE-A997-11DA-B012-B622A1EF5492')
2010-10-13 21:08:36,556 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'platform:Fixed MDIO bus')
2010-10-13 21:08:36,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'pci:v00008086d0000293Asv00001028sd000002AAbc0Csc03i20')
2010-10-13 21:08:36,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'serio:ty01pr00id00ex00')
2010-10-13 21:08:36,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw2,')
2010-10-13 21:08:36,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'pci:v00008086d00002939sv00001028sd000002AAbc0Csc03i00')
2010-10-13 21:08:36,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'input:b0019v0000p0000e0000-e0,1,k71,72,73,94,CA,E0,E1,E3,EC,F0,ramlsfw')
2010-10-13 21:08:36,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'input:b0000v0000p0000e0000-e0,5,kramlsfw4,')
2010-10-13 21:08:36,557 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0xa07312c> about HardwareID('modalias', 'acpi:device:')
2010-10-13 21:08:36,608 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-13 21:08:36,734 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-13 21:08:36,777 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-13 21:10:26,396 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-13 21:10:36,575 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-10-13 21:10:36,576 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-10-13 21:10:36,676 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-13 21:11:32,104 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-13 21:11:32,128 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-13 21:11:32,175 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-10-13 21:11:33,001 DEBUG: Shutting down

There's more above that, but I think what I pasted is enough

Any ideas?

---

### Post by johnnytm on 2010-10-13
were you connected to the internet when you tried to enable broadcom sta? I know it seems silly but worth making sure of. Type sudo lshw -C network in terminal and post the output.
You can also try to install from terminal. Just be sure your connected via wired connection before doing so. Try removing anything u installed first. Use this in terminal.

   ```

     sudo apt-get --purge remove bcmwl-kernel-source
    sudo apt-get install patch 
    sudo apt-get install bcmwl-kernel-source

```

---

### Post by nicvia on 2010-10-13
> **johnnytm said:**
> were you connected to the internet when you tried to enable broadcom sta? I know it seems silly but worth making sure of. Type sudo lshw -C network in terminal and post the output.
You can also try to install from terminal. Just be sure your connected via wired connection before doing so. Try removing anything u installed first. Use this in terminal.

   ```

     sudo apt-get --purge remove bcmwl-kernel-source
    sudo apt-get install patch 
    sudo apt-get install bcmwl-kernel-source

```

This is what it says while I'm on my wired connection:

*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 70:1a:04:aa:7f:c6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:93:6a:8b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=182.18.220.125 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)

Also, I tried the commands in terminal, rebooted, but still no hope. It recognizes my connection, I connect, it says 'Connection Established', but I can never connect to any websites.

---

### Post by nicvia on 2010-10-13
By the way, in 'Additional Drivers' it says that Broadcom STA wireless driver is now activated and currently in use, but i still cannot connect to my wireless connection.

---

### Post by johnnytm on 2010-10-13
that sounds like its not resolving dns names now, but at least your driver is working. post the output of ifconfig so we can see if it is connecting to the router at least.

---

### Post by nicvia on 2010-10-13
ifconfig says:


eth0      Link encap:Ethernet  HWaddr a4:ba:db:93:6a:8b  
          inet addr:182.18.220.125  Bcast:182.18.221.255  Mask:255.255.254.0
          inet6 addr: fe80::a6ba:dbff:fe93:6a8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5924 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6048473 (6.0 MB)  TX bytes:1122213 (1.1 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 70:1a:04:aa:7f:c6  
          inet6 addr: fe80::721a:4ff:feaa:7fc6/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:932
          TX packets:319 errors:52 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6554 (6.5 KB)  TX bytes:41149 (41.1 KB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13864 (13.8 KB)  TX bytes:13864 (13.8 KB)

---

### Post by johnnytm on 2010-10-13
check your connections settings in network manager use the edit button and look at your wireless connection, check ipv4 and check to see that it is set to automatic(dchp) because from what it looks like in your output, ipv4 is not working on your wireless card. but that could be simply because your not using it right now. post the output of ```
 lsmod | grep 'wl' 
``` and ```
 lspci -nn | grep 'Broadcom' 
``` btw ur wireless card is working. eth1 is the wireless card and it is transmitting and receiving according to ifconfig.

---

### Post by jazmanjal on 2010-10-13
just now I reply, just to share my reply here 
[http://ubuntuforums.org/showthread.php?p=9965747#post9965747](http://ubuntuforums.org/showthread.php?p=9965747#post9965747)

---

### Post by nicvia on 2010-10-13
> **johnnytm said:**
> check your connections settings in network manager use the edit button and look at your wireless connection, check ipv4 and check to see that it is set to automatic(dchp) because from what it looks like in your output, ipv4 is not working on your wireless card. but that could be simply because your not using it right now. post the output of ```
 lsmod | grep 'wl' 
``` and ```
 lspci -nn | grep 'Broadcom' 
``` btw ur wireless card is working. eth1 is the wireless card and it is transmitting and receiving according to ifconfig.

IPv4 in my wireless connection is set to automatic (DHCP).

lsmod | grep 'wl'says: 

wl                   1959565  0 
lib80211                5058  2 lib80211_crypt_tkip,wl

lspci -nn | grep 'Broadcom'says: 

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by johnnytm on 2010-10-13
There are two blacklist files for you to look at and post any broadcom entries in them. they are in etc/modprobe.d one is called blacklist.conf and the other should be blacklist-bcm43 can u find them and post any broadcom entries in there? That may show any driver conflicts.

---

### Post by nicvia on 2010-10-14
> **johnnytm said:**
> There are two blacklist files for you to look at and post any broadcom entries in them. they are in etc/modprobe.d one is called blacklist.conf and the other should be blacklist-bcm43 can u find them and post any broadcom entries in there? That may show any driver conflicts.

blacklist.conf:

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

blacklist-bcm43.conf:

# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

---

### Post by johnnytm on 2010-10-14
Seems the right drivers are blacklisted. Broadcom has a set of instructions here  [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) that may be helpful. there are some other solutions below the install instructions. [COLOR=#000080][URL="http://www.broadcom.com/docs/linux_sta/README.txt"]
[/URL][/COLOR]
[COLOR=#000080][URL="http://www.broadcom.com/docs/linux_sta/README.txt"]
[/URL][/COLOR]

---

### Post by nicvia on 2010-10-14
I don't get this part:

tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

Whenever I do that it says:

tar (child): /hybrid-portsrc-x86_32-v5.60.48.36.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

---

### Post by johnnytm on 2010-10-14
the tar files are the driver package files. unless you downloaded the drivers from there just ignore that part since it's just telling you how to build the driver for install. go below that to the part that deals with after the driver is installed.

---

### Post by nicvia on 2010-10-14
> **johnnytm said:**
> the tar files are the driver package files. unless you downloaded the drivers from there just ignore that part since it's just telling you how to build the driver for install. go below that to the part that deals with after the driver is installed.

Never mind, it works now! I don't know why, but I'm pretty sure it was because of your help! Thank you very much! :D

---

### Post by johnnytm on 2010-10-14
Glad to hear everything is working now. You might want to mark this thread as solved, Glad to help out.
Have fun with Ubuntu

---

