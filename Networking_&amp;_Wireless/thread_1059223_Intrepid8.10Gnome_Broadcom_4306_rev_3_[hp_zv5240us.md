---
title: "Intrepid/8.10/Gnome: Broadcom 4306 rev 3 [hp zv5240us]"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by nellmathew on 2009-02-03
Hey guys, I've been trying to get my wireless card to work on Hardy for about 2 weeks now. I finally gave up and upgraded to Intrepid hoping for better results. I've reformatted and reinstalled Ubuntu 3 times already since yesterday and tried several different methods/HowTos (I got a thing for clean installs, incase I messed anything up - which I seem to do often). Okay, so - anyone know how I can get this working? So far I've got a clean Intrepid [Gnome] install and the latest updates, nothing more. Here's some info to further assist anyone that can help:

**lspci -nn:**
```
00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon 9100 IGP Host Bridge [1002:5833] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc Radeon 9100 IGP AGP Bridge [1002:5838]
00:13.0 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #1 [1002:4347] (rev 01)
00:13.1 USB Controller [0c03]: ATI Technologies Inc OHCI USB Controller #2 [1002:4348] (rev 01)
00:14.0 SMBus [0c05]: ATI Technologies Inc SMBus [1002:4353] (rev 16)
00:14.1 IDE interface [0101]: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller [1002:4349]
00:14.3 ISA bridge [0601]: ATI Technologies Inc Device [1002:434c]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller [1002:4342]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP150 AC'97 Audio Controller [1002:4341]
00:14.6 Modem [0703]: ATI Technologies Inc IXP AC'97 Modem [1002:434d] (rev 01)
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP] [1002:5835]
02:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) [104c:8026]
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
02:03.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
02:04.0 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.1 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
02:04.2 System peripheral [0880]: Texas Instruments PCI1620 Firmware Loading Function [104c:8201] (rev 01)
02:07.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:07.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 43)
02:07.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 04)
```

**lshw -C network:**
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:05:0c:da
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.100 latency=128 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:5a:e4:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d6:e4:be:e9:a2:15
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

**lspci -v | less:**
```
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 12f4
        Flags: bus master, fast devsel, latency 64, IRQ 18
        Memory at d0204000 (32-bit, non-prefetchable) [size=8K]
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb
```

[COLOR="DarkOrange"][SIZE="5"]**Solved! check post #5 below.**[/SIZE][/COLOR]

---

### Post by nellmathew on 2009-02-04
Well, since the default drivers aren't working I tried installing ndiswrapper (again), cabextract and ndisgtk & using my windows driver from hp (sp29361); used cabextract to extract sp29361 and used "sudo ndisgtk" to install the inf. Driver was installed fine: said hardware present. I also blacklisted b43, b43legacy, ssb, and bcm43xx and on top of that I added ndiswrapper to "/etc/modules", hmm what else..  I did "sudo modprobe ndiswrapper" followed by "sudo ndiswrapper -m", and some other commands which were the same in most of the Broadcom Wifi HowTo guides. What else needs to be done? Can someone please help?

**ndiswrapper -l:** [COLOR="Blue"]the driver seems to be installed.[/COLOR]
```
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
```

I can't use "configure network" in ndisgtk - I guess I need to install a network configuration tool, can you guys recommend one for use later atleast?

**iwconfig:** [COLOR="Red"]as you can see, wlan0 no longer exists [it did with the b43 drivers, but those just didn't work!][/COLOR]
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

**lshw -C network:**[COLOR="Red"] as you can also see somehow b43 is still the driver!![/COLOR]
```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
```

Maybe I was supposed to somehow uninstall the default b43 packages that came installed with Intrepid? When I blacklisted the b43 packages; the wireless options disappeared from the Network Connections icon in the Gnome Panel so I figured that did the job.

---

### Post by Jack Harkness on 2009-02-04
Same card I have.  Never figured out how to make ndiswrapper work with it.  Try unblacklisting the b43 packages, then run "sudo apt-get install b43-fwcutter".  Then you should be able to use the native Linux driver with it.

---

### Post by lswest on 2009-02-04
run ```
sudo modprobe -r ssb b43
``` then ```
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```

it should work then.  If it does, add ssb to your blacklist file (/etc/modprobe.d/blacklist)

---

### Post by nellmathew on 2009-02-04
Thanks Jack Harkness! I reformatted one last time and decided to give the default drivers a go again, all I did was update my clean system, "sudo apt-get install b43-fwcutter" - and let it find and install the drivers. At first the drivers kept asking me for my WPA password over and over, I had this problem sometime last week before finally giving up. I simply tried disabling wireless (right click : uncheck "Enable Wireless") and renabling it again, and to my surprise I was able to connect using "Connect to Hidden Wiress Network" (since I don't broadcast my SSID). Cheers! Hope this can help someone, I know a lot of people are having wireless issues.

---

