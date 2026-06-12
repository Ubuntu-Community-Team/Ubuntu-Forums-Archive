---
title: "Unable to connect to an available network"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by _Stephen on 2011-07-05
Hi everyone, I'm new to all of this so bare with me. (plus sorry if this is in the wrong place, etc.)

I recently installed and now my wireless Internet isn't working.  I have a Dell Inspiron 1545 laptop, with the 1397 wlan mini card.  I have read through other threads, but I was unable to solve the problem I am having (Stated below).

I just installed ALL updates available and plugged in my computer to connect to the Internet.  Now the wireless option is there, and so is my network, but when I select it, nothing happens.

I will post whatever you guys need to see.

Thanks!

---

### Post by smurphy_it on 2011-07-05
Welcome to the forums.  I would suggest you take a peek at this for starters.

[https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-troubleshooting.html](https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-troubleshooting.html)

---

### Post by _Stephen on 2011-07-05
> **smurphy_it said:**
> Welcome to the forums.  I would suggest you take a peek at this for starters.

[https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-troubleshooting.html](https://help.ubuntu.com/11.04/ubuntu-help/net-wireless-troubleshooting.html)


Been through it, but thank you!  If you can help:  When I "connect" to the wireless I get a spinning wheel for a minute, then it asks for my password, and does the same thing again...  haha does that mean anything to you?

Edit: if it wouldn't be a problem, could I add you on msn and we could chat?

Thanks again.

---

### Post by smurphy_it on 2011-07-05
Sounds like the wrong driver.  Post the output of:

```
sudo lspci -k
```

---

### Post by _Stephen on 2011-07-05
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
    Subsystem: Dell Device 02aa
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02aa
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Device 02aa
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: uhci_hcd
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: uhci_hcd
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: uhci_hcd
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
    Subsystem: Dell Device 02aa
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
    Subsystem: Dell Device 02aa
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
    Subsystem: Dell Device 02aa
    Kernel modules: i2c-i801
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
    Subsystem: Dell Device 02aa
    Kernel driver in use: sky2
    Kernel modules: sky2
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card
    Kernel driver in use: wl
    Kernel modules: wl, ssb

---

### Post by smurphy_it on 2011-07-05
Follow this guide, then.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by nm_geo on 2011-07-05
Run this in terminal and paste result; Just copy and paste the line it is tough to retype that stuff.  What we are doing is checking to see if you have blacklisted modules that we may need.

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```You presently have the STA (wl) driver installed and the ssb module and I am told they conflict.  Most users are have more success with the b43-fwcutter and then the correct firmware.

---

### Post by _Stephen on 2011-07-05
> **smurphy_it said:**
> Follow this guide, then.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

*Still* not working... trying nm's idea now.

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Run this in terminal and paste result; Just copy and paste the line it is tough to retype that stuff.  What we are doing is checking to see if you have blacklisted modules that we may need.

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```You presently have the STA (wl) driver installed and the ssb module and I am told they conflict.  Most users are have more success with the b43-fwcutter and then the correct firmware.


# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
blacklist b43
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

---

### Post by nm_geo on 2011-07-05
Do the one listed above Stephen and add this one too please

```
lspci -nn
```

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Do the one listed above Stephen and add this one too please

```
lspci -nn
```

I believe I already did the one above, but here is the lspci -nn one...

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

---

### Post by 10snoopy1 on 2011-07-05
Which version of Ubuntu are you running?

---

### Post by _Stephen on 2011-07-05
> **10snoopy1 said:**
> Which version of Ubuntu are you running?

[http://tinypic.com/view.php?pic=dc33om&s=7](http://tinypic.com/view.php?pic=dc33om&s=7)

Hopefully that is what you need to see.
[IMG]http://tinypic.com/view.php?pic=dc33om&s=7[/IMG]

---

### Post by nm_geo on 2011-07-05
Ok we have a plan now..

I assume you are connected by ethernet cable correct?

If so deactivate the STA (wl) driver in Additional Drivers.

We are going to install in Synaptic .. Do a search on bcm in the search box after you start up Synaptic the below modules need to be installed.

b43-fwcutter
firmware-b43-lpphy-installer  

Then we will see if we need to comment out the blacklist lines.

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Ok we have a plan now..

I assume you are connected by ethernet cable correct?

If so deactivate the STA (wl) driver in Additional Drivers.

We are going to install in Synaptic .. Do a search on bcm in the search box after you start up Synaptic the below modules need to be installed.

b43-fwcutter
firmware-b43-lpphy-installer  

Then we will see if we need to comment out the blacklist lines.

Just did it... Now what should I do?  (wireless still isn't connecting)

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> Just did it... Now what should I do?  (wireless still isn't connecting)

Let's make sure where we are first.  Give us these two command results.please

```
sudo lshw -C network
```

```
rfkill list all
```

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Let's make sure where we are first.  Give us these two command results.please

```
sudo lshw -C network
``````
rfkill list all
```

-C Network:

```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:88:80:0d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:2d:90:ba
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.108 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)

```

rfkill:
```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> -C Network:

```
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:88:80:0d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:2d:90:ba
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.108 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)

```rfkill:
```
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

you still have the wl driver installed 

configuration: broadcast=yes[COLOR=Red] driver=wl0[/COLOR] driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg        resources: irq:17 memory:f69fc000-f69fffff

Go back to Synaptic do the search on bcm and remove any packet other than the b43-fwcutter and the firmware for the LLPY..  we only want those two we installed above.

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> you still have the wl driver installed 

configuration: broadcast=yes[COLOR=Red] driver=wl0[/COLOR] driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg        resources: irq:17 memory:f69fc000-f69fffff

Go back to Synaptic do the search on bcm and remove any packet other than the b43-fwcutter and the firmware for the LLPY..  we only want those two we installed above.

Here is what I have in Synaptics now: [http://tinypic.com/r/vyntx1/7](http://tinypic.com/r/vyntx1/7)

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> Here is what I have in Synaptics now: [http://tinypic.com/r/vyntx1/7](http://tinypic.com/r/vyntx1/7)

Let try a reboot now and see where we are please.

Then we will check the blacklist files and comment out any 
blacklist b43 
blacklist ssb

After reboot run the 
```

sudo lshw -C network 
```

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Let try a reboot now and see where we are please.

Then we will check the blacklist files and comment out any 
blacklist b43 
blacklist ssb

After reboot run the 
```

sudo lshw -C network 
```

```
*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:2d:90:ba
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.108 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
```

---

### Post by nm_geo on 2011-07-05
Ok it looks like we have blacklist junk to fix 

Try this first

```
sudo modprobe b43
```

and let's see if we get a temporary fix.. It will not stay fixed probably.

the let's do the long line again

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Ok it looks like we have blacklist junk to fix 

Try this first

```
sudo modprobe b43
```and let's see if we get a temporary fix.. It will not stay fixed probably.

the let's do the long line again

```
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|ssb|witch|wl'
```

After using the first command something popped up that said wifi found or something along those lines, but it still doesn't work.

Next command gave this:
```
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
blacklist wl
blacklist uart6850
blacklist twl4030_wdt
# wl module from Broadcom conflicts with ssb
blacklist b43legacy
blacklist b43
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
```

---

### Post by nm_geo on 2011-07-05
Ok suit up your sudo we are going in to fix those blacklist files.

```
gksudo gedit /etc/modprobe.d/*
```That command graphically open gedit with root rights.  You will see in the upper area files that are listed under the modprobe.d folder.  Look through the files and where you see 

blacklist b43   or blacklist ssb 

we are going to put # in front of the line 

example # blacklist b43 and # blacklist ssb

Then save the files that you modified and reboot.  We could remove the files but they are small and this method is easy.

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Ok suit up your sudo we are going in to fix those blacklist files.

```
gksudo gedit /etc/modprobe.d/*
```That command graphically open gedit with root rights.  You will see in the upper area files that are listed under the modprobe.d folder.  Look through the files and where you see 

blacklist b43   or blacklist ssb 

we are going to put # in front of the line 

example # blacklist b43 and # blacklist ssb

Then save the files that you modified and reboot.  We could remove the files but they are small and this method is easy.

Still unable to use wireless correctly.

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> Still unable to use wireless correctly.

Ok do the 

```
sudo modprobe b43
```

then 

```
sudo lshw -C network
```

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Ok do the 

```
sudo modprobe b43
```then 

```
sudo lshw -C network
```

Network:

```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:2d:90:ba
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.108 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:88:80:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-9-generic firmware=478.104 link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by nm_geo on 2011-07-05
Looks good to me let do this to be sure 

Three lines here. One at a time

```
sudo su 
echo b43 >> /etc/modules 
exit
```Then reboot without ethernet cable attached

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Looks good to me let do this to be sure 

Three lines here. One at a time

```
sudo su 
echo b43 >> /etc/modules 
exit
```Then reboot without ethernet cable attached

*Still* not connecting... Just shows the wheel spinning.

---

### Post by nm_geo on 2011-07-05
Let see this. Ethernet cable was detached correct? 
 
```

sudo iwlist scanning
```

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Let see this. Ethernet cable was detached correct? 
 
```

sudo iwlist scanning
```

It **was** unplugged, but I have to use it currently.

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:40:54:49
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-13 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ff387f32d
                    Extra: Last beacon: 284ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B00010310470010FEDF23B4C8D3CEAA8D0058CA8AB6D0A5102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180202F4050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 02 - Address: 00:12:17:CE:57:F7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fee4af9ffc
                    Extra: Last beacon: 8144ms ago
                    IE: Unknown: 0009000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000
          Cell 03 - Address: 00:26:50:B6:65:D1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"2WIRE671"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000020669a1ead81
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 00083257495245363731
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0E0050F204104A0001101044000102

vboxnet0  Interface doesn't support scanning.

```

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> It **was** unplugged, but I have to use it currently.

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:9C:40:54:49
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-13 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002ff387f32d
                    Extra: Last beacon: 284ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A00011010440001021041000100103B00010310470010FEDF23B4C8D3CEAA8D0058CA8AB6D0A5102100074C696E6B737973102300075752543136304E102400063132333435361042000234321054000800060050F2040001101100075752543136304E100800020084
                    IE: Unknown: DD090010180202F4050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000
          Cell 02 - Address: 00:12:17:CE:57:F7
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fee4af9ffc
                    Extra: Last beacon: 8144ms ago
                    IE: Unknown: 0009000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000
          Cell 03 - Address: 00:26:50:B6:65:D1
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"2WIRE671"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000020669a1ead81
                    Extra: Last beacon: 820ms ago
                    IE: Unknown: 00083257495245363731
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0E0050F204104A0001101044000102

vboxnet0  Interface doesn't support scanning.

```

Is the AP (access point) named linksys your wireless router?  You are able to scan wireless .  So it appears a matter of setup to the wireless AP. Right click on the wifi symbol and fill in the info.

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Is the AP (access point) named linksys your wireless router?  You are able to scan wireless .  So it appears a matter of setup to the wireless AP. Right click on the wifi symbol and fill in the info.

1. When I right click it acts like I am left clicking.
2. What am I supposed to fill in?

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> 1. When I right click it acts like I am left clicking.
2. What am I supposed to fill in?

Verify Enable Wireless

Do see create new wireless ?

You need to add the information for your wireless connection.
Network Name
Wireless security
Key or passphrase
I am only users here so I always set mine to auto connect and available to all users.

---

### Post by nm_geo on 2011-07-05
Here are a couple of screenshot of my wireless setup. I ain't scared LOL.

The other pages i just leave untouched.

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Here are a couple of screenshot of my wireless setup. I ain't scared LOL.

The other pages i just leave untouched.

Exactly what mine looks like... :(

Also, how did you leave photos for me to view... is there a code I use to do that (instead of uploading them to tinypic, etc.)

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> Exactly what mine looks like... :(

Also, how did you leave photos for me to view... is there a code I use to do that (instead of uploading them to tinypic, etc.)

click Manage Attachments below the message box..  

So you are still not able to connect wireless?  The Network Manager will not allow wireless if you are using a wired connection. So you must have the cable removed to use wireless.  Since you can scan you should be able to connect now.

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> click Manage Attachments below the message box..  

So you are still not able to connect wireless?  The Network Manager will not allow wireless if you are using a wired connection. So you must have the cable removed to use wireless.  Since you can scan you should be able to connect now.

Took out the ethernet cord, still doesn't work. Made a new network, still doesn't work. It says it's connected (screenshot) but nothing loads!

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> Took out the ethernet cord, still doesn't work. Made a new network, still doesn't work. It says it's connected (screenshot) but nothing loads!

With cable disconnected ..

```
sudo lshw -C network

```
```
nm-tool
```

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> With cable disconnected ..

```
sudo lshw -C network

``````
nm-tool
```


Network:
```
*-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:2d:90:ba
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:88:80:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-9-generic firmware=478.104 ip=10.42.43.1 link=yes multicast=yes wireless=IEEE 802.11bg

```NM-tool:
```
State: connected

- Device: wlan0  [linksys] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           no
  HW Address:        00:22:5F:88:80:0D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    linksys:         Ad-Hoc, 00:00:00:00:00:00, Freq 2412 MHz, Rate 0 Mb/s, Strength 0 WPA
    linksys:         Infra, 00:25:9C:40:54:49, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         10.42.43.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0



- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:23:AE:2D:90:BA

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


```

ALSO: my docks keep disappearing... wtf?

---

### Post by nm_geo on 2011-07-05
Do you happen to have any other computers on your wireless access point?  I am not used to that 
ip=10.42.43.1

Try to

```
 ping -c 3 8.8.8.8
```Wireless and then wired.

Is the wireless setup to DHCP server?

---

### Post by nm_geo on 2011-07-05
Did you build that page like mine..

Or did you select AD-HOC try Infrastructure

see pic

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Do you happen to have any other computers on your wireless access point?  I am not used to that 
ip=10.42.43.1

Try to

```
 ping -c 3 8.8.8.8
```Wireless and then wired.

Is the wireless setup to DHCP server?

There are 2 other computers using the same wireless as I am... The 2 other people in my house.  As for using Ping - wired:
```
ING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=45 time=112 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=45 time=111 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=45 time=109 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 109.951/111.047/112.132/0.970 ms

```

wire disconnected: connect: Network is unreachable

---

### Post by nm_geo on 2011-07-05
Check out this link 

[http://ubuntuforums.org/showthread.php?t=1388206](http://ubuntuforums.org/showthread.php?t=1388206)

See if that helps.

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Check out this link 

[http://ubuntuforums.org/showthread.php?t=1388206](http://ubuntuforums.org/showthread.php?t=1388206)

See if that helps.

STILL doesn't work... are you getting more and more frustrated like I am? :P

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> STILL doesn't work... are you getting more and more frustrated like I am? :P
 
Well when i look back at your wired IP on one of the first lshw runs i see a normal looking ip.  You are setup wrong either in the Network Manager settings or the wireless router.  Since others are connected to the wireless AC I got to think it is the setup.  Check the picture above for your IPv4 Settings.. Make it look like mine.

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Well when i look back at your wired IP on one of the first lshw runs i see a normal looking ip.  You are setup wrong either in the Network Manager settings or the wireless router.  Since others are connected to the wireless AC I got to think it is the setup.  Check the picture above for your IPv4 Settings.. Make it look like mine.

Just did that. Still nothing.

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> Just did that. Still nothing.

okay reboot without cable ...

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> okay reboot without cable ...

When I first logged on it connected for about 5 seconds, then disconnected.

SO CLOSE!

---

### Post by nm_geo on 2011-07-05
> **_Stephen said:**
> When I first logged on it connected for about 5 seconds, then disconnected.

SO CLOSE!

```
Do this paste results 

dmesg | egrep 'ound|irmware|eth|ath|wl|ipw|b43|witch|ndiswrapper'
```

```
sudo lshw -C network
```

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> ```
Do this paste results 

dmesg | egrep 'ound|irmware|eth|ath|wl|ipw|b43|witch|ndiswrapper'
``````
sudo lshw -C network
```

```
witch|ndiswrapper'
[    0.204136] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.324245] ACPI: No dock devices found.
[    0.324250] HEST: Table not found.
[    0.408087] Switching to clocksource hpet
[    0.411878] Switched to NOHz mode on CPU #0
[    0.411961] Switched to NOHz mode on CPU #1
[    0.453125] pnp: PnP ACPI: found 12 devices
[    0.506585] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.556023] ACPI: Lid Switch [LID]
[    0.627872] ERST: Table is not found!
[    1.025842] isapnp: No Plug & Play device found
[    1.060117] i2c-core: driver [adp5520] using legacy suspend method
[    1.060119] i2c-core: driver [adp5520] using legacy resume method
[    1.080170] hub 1-0:1.0: USB hub found
[    1.100149] hub 2-0:1.0: USB hub found
[    1.100521] hub 3-0:1.0: USB hub found
[    1.100854] hub 4-0:1.0: USB hub found
[    1.104183] hub 5-0:1.0: USB hub found
[    1.104496] hub 6-0:1.0: USB hub found
[    1.104809] hub 7-0:1.0: USB hub found
[    1.105123] hub 8-0:1.0: USB hub found
[    1.134572] device-mapper: multipath: version 1.2.0 loaded
[    1.134575] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.138544] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.352913] sky2 0000:09:00.0: eth0: addr 00:23:ae:2d:90:ba
[    1.874793] Console: switching to colour frame buffer device 170x48
[    1.875694] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   22.232206] lp: driver loaded but no devices found
[   22.646202] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.646219] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   22.676324] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[   22.676342] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[   22.676360] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[   22.676378] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[   22.845876] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[   22.856626] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   23.081390] Registered led device: b43-phy0::tx
[   23.081416] Registered led device: b43-phy0::rx
[   23.081441] Registered led device: b43-phy0::radio
[   23.081460] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   23.234873] uvcvideo: Found UVC 1.00 device Integrated_Webcam_1.3M (0c45:63ee)
[   23.345075] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   23.345322] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   23.722028] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   23.957723] vboxdrv: Found 2 processor cores.
[   29.380636] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   29.380641] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[   29.380644] b43-phy0: Controller RESET (DMA error) ...
[   29.608443] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   35.225636] b43-phy0: Controller restarted
[   35.233112] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.241005] sky2 0000:09:00.0: eth0: enabling interface
[   35.243071] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.212850] wlan0: authenticate with 00:25:9c:40:54:49 (try 1)
[   55.214616] wlan0: authenticated
[   55.214956] wlan0: associate with 00:25:9c:40:54:49 (try 1)
[   55.217505] wlan0: RX AssocResp from 00:25:9c:40:54:49 (capab=0x401 status=0 aid=1)
[   55.217508] wlan0: associated
[   55.218903] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   61.304260] ieee80211 phy0: wlan0: No probe response from AP 00:25:9c:40:54:49 after 500ms, disconnecting.
[   62.696823] wlan0: authenticate with 00:25:9c:40:54:49 (try 1)
[   62.896050] wlan0: authenticate with 00:25:9c:40:54:49 (try 2)
[   63.096050] wlan0: authenticate with 00:25:9c:40:54:49 (try 3)
[   63.296036] wlan0: authentication with 00:25:9c:40:54:49 timed out
[   65.248032] wlan0: no IPv6 routers present
[  141.460086] sky2 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[  141.460265] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  152.064067] eth0: no IPv6 routers present
[  234.750196] sky2 0000:09:00.0: eth0: Link is down
[  305.463017] sky2 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[  414.217619] sky2 0000:09:00.0: eth0: Link is down

```


```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:2d:90:ba
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:88:80:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-9-generic firmware=478.104 link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by nm_geo on 2011-07-05
Yes i am also getting frustrated and need to go soon.

```
lsmod
```

reboot without cable 
```

ifconfig
```

---

### Post by _Stephen on 2011-07-05
> **nm_geo said:**
> Yes i am also getting frustrated and need to go soon.

```
lsmod
```reboot without cable 
```

ifconfig
```

```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
dm_crypt               22463  0 
vboxnetadp             13348  0 
vboxnetflt             27855  0 
vboxdrv               238410  2 vboxnetadp,vboxnetflt
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  4 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_intel,snd_hda_codec
uvcvideo               66851  0 
snd_seq_midi           13132  0 
joydev                 17322  0 
dell_wmi               12601  0 
videodev               75143  1 uvcvideo
snd_rawmidi            25269  1 snd_seq_midi
arc4                   12473  2 
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
b43                   296610  0 
dcdbas                 14054  1 dell_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73312  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              257001  1 b43
ssb                    45942  1 b43
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
cfg80211              156212  2 b43,mac80211
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527388  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41704  0 
usb_storage            43946  0 
hid                    77084  1 usbhid
uas                    17676  0 
i915                  450944  3 
sky2                   49172  0 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
ahci                   21591  3 
libahci                25548  1 ahci
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
ramzswap               13202  0 
xvmalloc               13453  1 ramzswap

```

rebooting now. Leave whenever, I will look elsewhere.

---

### Post by nm_geo on 2011-07-05
[   62.696823] wlan0: authenticate with [COLOR=Red]00:25:9c:40:54:49 [/COLOR](try 1) [   62.896050] wlan0: authenticate with 00:25:9c:40:54:49 (try 2) [   63.096050] wlan0: authenticate with 00:25:9c:40:54:49 (try 3) [   63.296036] wlan0: authentication with 00:25:9c:40:54:49 timed out

That red lettered stuff is your wireless router MAC we are not getting 
authenticated from it for some reason.

---

### Post by smurphy_it on 2011-07-11
disregard

---

