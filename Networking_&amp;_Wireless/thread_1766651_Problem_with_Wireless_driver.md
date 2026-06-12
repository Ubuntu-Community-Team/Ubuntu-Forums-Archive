---
title: "Problem with Wireless driver"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by SimonWesley on 2011-05-24
I use Ubuntu 10.04
My wireless driver seem to be connected to my router, but I can't access Internet. I tried to use  troubleshooting for wireless drivers but it didn't work out.
What can I do to find the answer to this?

---

### Post by garvinrick4 on 2011-05-24
Open a terminal and run this please.
```
sudo lshw -C network
```
Post results of this on this thread

---

### Post by fijianheadhunter on 2011-05-25
Hi, I have a similar problem. The following code is displayed when I use "sudo lshw -C network" ....


PCI (sysfs)  

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:03:4e:c4
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)


[end code]

When I open up "Additional Drivers" it shows "Broadcom STA wireless driver" - "This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, ..." etc. 

My computer is a HP Pavilion dv6000 - with some upgraded hardware. Thanks in advance


****** PROBLEM SOLVED ******* I tried several solutions from multiple forums: I think it was #13 from [https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010) that fixed my problem.

---

### Post by voodoomaggie on 2011-05-25
I'm having the same problem, I've been trying to fix it all day I just can't seem to figure it out. Please help and sorry to butt in

*-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:e2:68:b0
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.2.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:22:69:0e:78:93
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe7fc000-fe7fffff

---

### Post by SimonWesley on 2011-05-25
> **garvinrick4 said:**
> Open a terminal and run this please.
```
sudo lshw -C network
```Post results of this on this thread

When I try sudo lshw -C network in terminal I get this:

*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:98:cf:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:98700000-98703fff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:85:00.0
       logical name: eth0
       version: 00
       serial: 00:22:64:7c:3f:84
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.129 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:98600000-98603fff ioport:2000(size=256)

---

### Post by garvinrick4 on 2011-05-25
OPen Synaptic package installer. And the 2 I have highlighted you can read that
they are for Broadcom cards. Just type BCM in the upper right of Synaptics and it
will bring you there. Right click on them mark for installation and then hit the apply arrow.

---

### Post by SimonWesley on 2011-05-26
I have done as you said. It still doesn't work though. It connects to my router but doesn't connect to the internet. Trying sudo lshw -C network again gave this:

*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:98:cf:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:98700000-98703fff
  *-network
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:85:00.0
       logical name: eth0
       version: 00
       serial: 00:22:64:7c:3f:84
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.129 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:98600000-98603fff ioport:2000(size=256)

---

### Post by garvinrick4 on 2011-05-26
Did you restart the machine?
Give her a stop and a restart maybe the reboot will help.

```
sudo service network-manager stop
``````
sudo rm /var/lib/NetworkManager/NetworkManager.state
``````
sudo service network-manager start
```

---

### Post by chili555 on 2011-05-26
> *-network
description: Wireless interface
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth1
version: 01
serial: 00:21:00:98:cf:5f
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 [COLOR="Red"]ip=10.42.43.1[/COLOR] latency=0 multicast=yes wireless=IEEE 802.11bg
resources: irq:17 memory:98700000-98703fffThat IP address is typical of a computer-to-computer or internet connection sharing arrangement. Did you click the Network Manager icon, Edit Connections and Create New Wireless Network...? That wording actually ought to say, "Create Ad-Hoc Computer-to-Computer Network."

Is that what you intended? I didn't think so. Please wipe out all those settings and immediately reboot. Then let Network Manager find your router and connect.

---

### Post by garvinrick4 on 2011-05-26
```
sudo ifconfig wlan0
``` (yours says eth1)
```
sudo ifconfig wlan0 up
```
```
iwlist wlan0 scan
```

---

### Post by chili555 on 2011-05-26
> (yours says eth1)So why are you asking for commands with wlan0?

---

### Post by SimonWesley on 2011-05-26
Thanks! It works now after deleting the connection to the router and trying again. What a relief!

---

### Post by fijianheadhunter on 2011-06-12
Bummer! I was working on another problem (slow internet probably caused by driver issues) an I activated "Broadcom STA wireless driver" in Additional Drivers and then my wireless turned off. Now I can't figure out how to fix the problem... seems to be the same kind of issue that I fixed two weeks ago. here is what I have for "sudo lshw -C network":

  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d6000000-d6003fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 02
       serial: 00:1b:24:03:4e:c4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=204.210.110.90 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:d8000000-d8000fff ioport:4000(size=64)




Got the following with an error when I was trying to reinstall STA driver (following instructions in [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)) with "sudo apt-get install bcmwl-kernel-source" in terminal. 

lnakatsu@lnakatsu-HP-Pavilion-dv6000-RX019AV-ABA:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-program-options1.42.0 libboost-thread1.42.0
  libboost-date-time1.42.0 libkprintutils4 gstreamer0.10-fluendo-mp3 liboil0.3
  gnash-common libkutils4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

I think I need "firmware-b43-lpphy-installer". Is that correct? Synaptic Package Manager shows that it is already installed.

---

### Post by chili555 on 2011-06-12
> I think I need "firmware-b43-lpphy-installer". Is that correct? No. Just the reverse.> Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.The install process is telling you that you do *NOT* have a lp-phy chipset, so installing that firmware won't work. Moreover, your device is claimed by both wl and b43/ssb. If bcmwl-kernel-source got installed, completely remove it.

Then install b43-fwcutter, the proper firmware referred to. Then reboot and tell us how your wireless is working.

---

### Post by fijianheadhunter on 2011-06-13
Just tried to completely remove "bcmwl-kernel-source" via Synaptic Package Manager and got the following error: 

(Reading database ... 289075 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer


--- However now Synaptic Package Manager is showing that it is not installed. How do you know if it is completely removed? I will assume it is for now. 

Next, I reinstalled b43-fwcutter in Synaptic Package Manager and got a similar error... 

(Reading database ... 289027 files and directories currently installed.)
Preparing to replace b43-fwcutter 1:013-3 (using .../b43-fwcutter_1%3a013-3_i386.deb) ...
Unpacking replacement b43-fwcutter ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:013-3) ...
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer


-- I checked and found that "firmware-b43-lpphy-installer" was installed. So I completely removed it via SPM (Synaptic Package Manager) ---> no errors. Next, I tried to reinstall b43-fwcutter to see if I would get an error again ---> no errors this time. I'm going to restart my computer and see if wireless is back.

-- Restarted, but no wireless. What should I try next? The wireless went down right after I was in Additional Drivers and activated Broadcom STA wireless driver. Right now this driver is deactivated. Should I activated it? Let me try that. 

-- Activated now and restarted but no wireless.  ... I have a  BCM4311 wireless card and found another thread ([http://linuxfloat.org/bcm4311-wireless-card-not-working](http://linuxfloat.org/bcm4311-wireless-card-not-working)) that says to remove Broadcom STA driver. Therefore I'm going to remove it. It also says to install "firmware-b43-installer" ---> just installed it.

---

### Post by chili555 on 2011-06-13
You should have b43-fwcutter and nothing else installed. The modules that should be loaded are b43 and ssb. Let's check:```
lsmod | grep -e b43 -e ssb
```Are they both loaded? If not, it could be because the installation of bcmwl-kernel-source blacklists some b43 and b43legacy modules. Let's check:```
ls /etc/modprobe.d
```If there are any b43 items, stop and ask me if we need to remove them. 

In that case, let's load the modules:```
sudo modprobe b43 ssb
```Now is your wireless working? If so, I think we'll need to look at the b43 blacklists before we proceed with a permanent fix.

If your wireless does not work after loading b43 and ssb, let's see why:```
dmesg | grep -e wlan -e b43
```> says to remove Broadcom STA driver. Therefore I'm going to remove it.You already did when you removed bcmwl-kernel-source, didn't you?

I hope you will stop and ask before you make more changes.

---

### Post by fijianheadhunter on 2011-06-13
> **chili555 said:**
> You should have b43-fwcutter and nothing else installed. The modules that should be loaded are b43 and ssb. Let's check:```
lsmod | grep -e b43 -e ssb
```

This is what I got: 
```
lnakatsu@lnakatsu-HP-Pavilion-dv6000-RX019AV-ABA:~$ lsmod | grep -e b43 -ssb
206:b43                   296610  0 
558:mac80211              257001  1 b43
945:cfg80211              156212  2 b43,mac80211
1583:ssb                    45942  1 b43

```Should I have "mac80211" or "cfg80211"? 

> **chili555 said:**
> 
Are they both loaded? If not, it could be because the installation of bcmwl-kernel-source blacklists some b43 and b43legacy modules. Let's check:```
ls /etc/modprobe.d
```If there are any b43 items, stop and ask me if we need to remove them. 


Here is what I got: 
```

lnakatsu@lnakatsu-HP-Pavilion-dv6000-RX019AV-ABA:~$ ls /etc/modprobe.d
alsa-base.conf          blacklist-firewire.conf     blacklist-oss.conf
blacklist               blacklist-framebuffer.conf  blacklist-rare-network.conf
blacklist-ath_pci.conf  blacklist-local.conf        blacklist-watchdog.conf
blacklist.conf          blacklist-modem.conf

```No b43. 

> **chili555 said:**
> 
In that case, let's load the modules:```
sudo modprobe b43 ssb
```Now is your wireless working? If so, I think we'll need to look at the b43 blacklists before we proceed with a permanent fix.

Per your request, I will stop at this point for further direction. I'm not sure which "case" you mean here. Should I load the modules if there is no b43 or there is b43? 

> **chili555 said:**
> 
If your wireless does not work after loading b43 and ssb, let's see why:```
dmesg | grep -e wlan -e b43
```You already did when you removed bcmwl-kernel-source, didn't you?

(I have not run the command above (yet), I am just quoting it for reference to answer your question) I did not run the above command when I removed "bcmwl-kernel-source". I removed it in Synaptic but received an error which I included in my previous post: 
> (Reading database ... 289075 files and directories currently installed.)
Removing bcmwl-kernel-source ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firmware-b43-lpphy-installer (4.174.64.19-5) ...
Not supported card here (PCI id 14e4:4311)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installerAfter the error, the file seems to have been removed since Synaptic doesn't give me an option to mark "bcmwl-kernel-source" for removal now (It only allows me to mark the file for installation). 

> **chili555 said:**
> 
I hope you will stop and ask before you make more changes.
Will do, sorry about that. Thanks for your patience.

---

### Post by chili555 on 2011-06-14
> Here is what I got:
```
lnakatsu@lnakatsu-HP-Pavilion-dv6000-RX019AV-ABA:~$ ls /etc/modprobe.d
alsa-base.conf          blacklist-firewire.conf     blacklist-oss.conf
blacklist               blacklist-framebuffer.conf  blacklist-rare-network.conf
blacklist-ath_pci.conf  blacklist-local.conf        blacklist-watchdog.conf
blacklist.conf          blacklist-modem.conf

```
No b43. Perfect! As well, b43 and ssb are loaded correctly. mac80211 and cfg80211 are required by b43 and are properly loaded. 

So, is your wireless working as expected? If not, please post:```
dmesg | grep -e wlan -e b43
```Thanks.

---

### Post by fijianheadhunter on 2011-06-14
Wireless external indicating light is now on (good sign). but connection menu says "Wireless network", "device not managed". 

Here is the results of command "dmesg | grep -e wlan -e b43":

nakatsu@lnakatsu-HP-Pavilion-dv6000-RX019AV-ABA:~$ dmesg | grep -e wlan -e b43
[    1.360617] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.360630] b43-pci-bridge 0000:02:00.0: setting latency timer to 64
[   22.930650] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   23.126178] Registered led device: b43-phy0::tx
[   23.126208] Registered led device: b43-phy0::rx
[   23.126239] Registered led device: b43-phy0::radio
[   23.728123] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   23.826802] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.056056] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   24.147722] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   85.248078] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   85.325205] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27946.026863] b43-pci-bridge 0000:02:00.0: PCI INT A disabled
[27947.001045] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[27947.001074] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd6000000)
[27947.001082] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[27947.001092] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[27947.083561] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[27949.344031] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[32989.872431] b43-pci-bridge 0000:02:00.0: PCI INT A disabled
[32990.801034] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[32990.801063] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd6000000)
[32990.801071] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[32990.801081] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[32990.877081] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[32993.128064] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[46334.484125] b43-pci-bridge 0000:02:00.0: PCI INT A disabled
[46335.465037] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[46335.465067] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xd6000000)
[46335.465074] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[46335.465084] b43-pci-bridge 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[46335.564795] b43-pci-bridge 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[46337.768041] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

I think we are close. Thanks in advance.

---

### Post by fijianheadhunter on 2011-06-15
Sorry, I needed my wireless back asap so I tried using some other threads to find a solution. Good news: Wireless is working now. Thank you for your help Chili555 - couldn't have done it without you. 

I changed two things that I think solved the problem: 
1. use ```
 sudo gedit /etc/modprobe.d/blacklist.conf 
``` And then put a "#" in front of the line: "blacklist bcm43xx" (if that line isn't already commented out)


2. Follow instructions in this thread: [http://www.accretionlogistics.com/2011/04/ubuntu-11-04-fix-the-wireless-device-not-managed/](http://www.accretionlogistics.com/2011/04/ubuntu-11-04-fix-the-wireless-device-not-managed/)

3. Reboot

---

### Post by boring2 on 2011-06-16
Chili555,
  I have been reading and reading and this post seemed to help the most, however I am still not there.  I was able to get the wireless to show DISABLED now instead of UNCLAIMED, but am stuck there.  

I ran the ls /etc/modprobe.d and it does show one file that is blacklist-bcm43.conf

```
benton@Timeline:~$ ls /etc/modprobe.d/
alsa-base.conf          blacklist-firewire.conf     blacklist-rare-network.conf
blacklist-ath_pci.conf  blacklist-framebuffer.conf  blacklist-watchdog.conf
blacklist-bcm43.conf    blacklist-modem.conf
blacklist.conf          blacklist-oss.conf
```

Here is the output for the sudo lshw -C network command

 ```
 *-network DISABLED
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 5c:ac:4c:8a:1f:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d2403fff

```

Thanks from a newbee.

---

### Post by chili555 on 2011-06-16
> I was able to get the wireless to show DISABLED now instead of UNCLAIMED, but am stuck there.Let's have a peek at:```
rfkill list all
dmesg | grep wl
```Thanks.

---

### Post by boring2 on 2011-06-16
```
benton@Timeline:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
benton@Timeline:~$ dmesg | grep wl
[    8.632007] wl: module license 'MIXED/Proprietary' taints kernel.
[    8.640058] wl 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.640068] wl 0000:02:00.0: setting latency timer to 64

```

What is this telling me?

---

### Post by chili555 on 2011-06-16
It's suggesting that the module acer-wmi thinks your key combination, Fn+F5 for example, has the wireless switched off:> 0: acer-wireless: Wireless LAN
    [COLOR="Red"]Soft blocked: yes[/COLOR]
    Hard blocked: noLet's try something:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Now is your wireless working? If so, we can tweak a couple of files to make it persistent.

---

### Post by boring2 on 2011-06-16
Amazing!!!  yes, it works, shows up, when I go and enable wireless it shows the networks and I am able to connect to the internet.  So now how do I make it persistent?

Thanks for the help btw...

---

### Post by chili555 on 2011-06-16
Please see post #6 here. It's the same problem and the same fix. Post back if you need further assistance.

[http://ubuntuforums.org/showthread.php?t=1783905](http://ubuntuforums.org/showthread.php?t=1783905)

---

