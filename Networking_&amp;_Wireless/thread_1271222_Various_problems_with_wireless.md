---
title: "Various problems with wireless"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by jeree on 2009-09-20
I'm having problems connecting to wireless network. I just switched over from windows, so I'm not experienced user. Anyway, sometimes I manage to connect to wireless network and sometimes can't. Those times when I manage, the connections is lost some time after. Also, when I used 13 letter password I couldn't get any connection. I wanted to try to use Windows Wireless Drivers, but I couldn't determine my Wireless card. So here are some questions:
1) How to I determine my Wireless card (what exactly am I suppose to look in lspci, is it Ethernet Controller or something else)?
2) Are there any other options other than Windows Wireless Drivers?
lspci
P.S. wired connection works perfectly.

---

### Post by Metaljaz on 2009-09-20
Lets determine what type of chipset your wireless has before you install windows drivers. Type lspci in the terminal and look for a line that looks similar to this one:

0c:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

This line tells you the wireless card and the chipset. From here we can help you determine what you need to do.
Post the results

---

### Post by jeree on 2009-09-21
It should be:
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)

Just in case the entire lspci:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
00:09.1 SD Host controller: ENE Technology Inc ENE PCI SmartMedia / xD Card Reader Controller
00:09.3 FLASH memory: ENE Technology Inc ENE PCI Secure Digital / MMC Card Reader Controller
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
```

---

### Post by Metaljaz on 2009-09-21
Okay I don't see wireless in that output. What I see is the ethernet which is the wired info. Try this command in the terminal and post the results: Again looking for wireless

sudo lshw -C network

---

### Post by jeree on 2009-09-22
```
  *-network
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:90:f5:80:f2:8c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:cc:d7:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:66:83:5d:38:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by Metaljaz on 2009-09-22
*-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:cc:d7:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

After looking here still no product or vendor listed. Need to identify the wireless card and chipset so that we can recommend the right drivers.
This command should give us the results we are looking for. In a terminal windows type the following command: (post the results)

lspci | grep Network

---

### Post by bkratz on 2009-09-22
> **Metaljaz said:**
> *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:cc:d7:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

After looking here still no product or vendor listed. Need to identify the wireless card and chipset so that we can recommend the right drivers.
This command should give us the results we are looking for. In a terminal windows type the following command: (post the results)

lspci | grep Network



Could it be a USB dongle and need lsusb?

---

### Post by Metaljaz on 2009-09-23
In the case of usb type this in the terminal:
lsusb

---

### Post by jeree on 2009-09-23
lspci | grep Network output was empty.

lsusb:
```
Bus 001 Device 003: ID 041e:4117 Creative Technology, Ltd Nomad MuVo TX
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
I guess it is RTL8187B.

---

### Post by Metaljaz on 2009-09-23
Thats it. Forgot all about the fact that it could have been usb. Thanks bkratz for the reminder.

read these post:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

[http://ubuntuforums.org/showthread.php?t=709802](http://ubuntuforums.org/showthread.php?t=709802)

[http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/](http://quilombo.wordpress.com/2008/03/07/realtek-rtl8187b-working-in-ubuntu-710-using-ndiswrapper/)

---

### Post by jeree on 2009-09-24
> First off if you should be using the Windows 98 driver with NDISwrapper. It is the only on at this point that is known to work.
Is this still true? Or even if it isn't does it make any difference if I use XP drivers?

---

### Post by bkratz on 2009-09-24
> **jeree said:**
> Is this still true? Or even if it isn't does it make any difference if I use XP drivers?



The sticky at the top of the page in this sections seems to indicate that is true, but it does seem to be a little old.  It does give a useful link to known working drivers though.  

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB)

I will look some more to make sure though.




This looks like much more current info (and really long!) look at posting #260
[http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187B](http://ubuntuforums.org/showthread.php?t=792092&highlight=RTL8187B)

---

### Post by jeree on 2009-09-26
If I undestand correctly I'm only suppose to follow one way? I mean if I use post #260 then I shouldn't be using ndiswrapper? I used files at post #260 and installation Method 1:
```
<<Method 1>>
Runing the scripts can finish all operations of building up modules
from the source code, installing driver to the kernel and starting up the nic.
        1. Build up the drivers from the source code
           make

        2. Install the driver to the kernel
           make install
           reboot
    
        3. bring up wlan if nic is not brought up by GUI, such as NetworkManager
           ifconfig wlan0 up
           Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to 
           check your wlan interface name,since it may change wlan0 to wlan1,etc.

```Some info in case I've made mistakses. I unistalled ndiswrapper. If I understand correctly then I'm suppose to run 'make' and 'make install' from terminal (I used sudo on 'make install'). I get the following error when I try use 'ifconfig wlan0 up':
```
wlan0: ERROR while getting interface flags: No such device
```The output of iwconfig is:
```

lo    no wireless extensions.

eth0     no wireless extensions.

pan0    no wireless extensions.


```

---

### Post by Metaljaz on 2009-09-26
You may have to try this. It was taken from another post:

Try issuing the following commands after loading the driver with ndiswrapper -i

Code:

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

Also add:

Code:

ndiswrapper

To the /etc/modules file. That will guarantee ndiswrapper is loading on startup.

---

### Post by jeree on 2009-09-27
Should I unistall what was posted in #260 before using ndiswrapper again?

---

