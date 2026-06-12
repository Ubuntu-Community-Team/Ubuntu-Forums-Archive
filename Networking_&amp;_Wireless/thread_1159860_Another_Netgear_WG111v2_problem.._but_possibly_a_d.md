---
title: "Another Netgear WG111v2 problem.. but possibly a deeper problem"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by nullhility on 2009-05-15
I was asked by my mother's boyfriend to redesign a website for the apartments he manages, he set me up in a room and tossed me a Netgear WG111v2 and a sheet of paper with a username, password, etc. After hooking my computer up (Ubuntu Jaunty distro/Gnome desktop) and plugging the dongle in nothing happened; so ensued a lengthly quest on his laptop to unravel this mystery.

I discovered that the drivers required weren't open source and I'd need to use Ndiswrapper to get the job done. But I ran into some problems... hence the post :)

Notes: I'm not networking inclined, this is - believe it or not - the first time I've played around with wireless and ndiswrapper.

So here's a copy paste of an attempt at reinstalling the drivers, I've tried to be verbose as possible and the methods used are somewhat collected from many posts across the internet.

```

~/Desktop/RTL8187/WIN98$ lsusb
Bus 004 Device 002: ID 046e:52c1 Behavior Tech. Computer Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c049 Logitech, Inc. G5 Laser Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)

~/Desktop/RTL8187/WIN98$ cat /etc/modprobe.d/blacklist
blacklist islsm_pci
blacklist islsm
blacklist islsm_usb
blacklist prism2_usb
blacklist rtl8187
blacklist r8187b
blacklist r8187

~/Desktop/RTL8187/WIN98$ sudo ndiswrapper -i Netrtuw.inf
installing netrtuw ...

~/Desktop/RTL8187/WIN98$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netrtuw : driver installed
	device (0846:6A00) present (alternate driver: rtl8187)

~/Desktop/RTL8187/WIN98$ sudo ndiswrapper -mi
module configuration information is stored in /etc/modprobe.d/ndiswrapper

~/Desktop/RTL8187/WIN98$ sudo ndiswrapper -ma
module configuration information is stored in /etc/modprobe.d/ndiswrapper

~/Desktop/RTL8187/WIN98$ sudo ndiswrapper -m
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive

~/Desktop/RTL8187/WIN98$ sudo depmod -a

~/Desktop/RTL8187/WIN98$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ndiswrapper

~/Desktop/RTL8187/WIN98$ modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

~/Desktop/RTL8187/WIN98$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

wlan0 inet dhcp

```

---

### Post by nullhility on 2009-05-15
Oh and the general consensus that I gleaned from the internet is that the Netgear adapter I have doesn't have open source drivers and is thus generally not supported by linux. So what's a wireless dongle I can buy (if this netgear model is a failure) that does have open source drivers and works best on linux?

---

### Post by LucaAltieri on 2009-05-22
Hi there,

Complete n00b myself but I think I have discovered a fix for this.

1) download the windows drivers from the Netgear site:

[ftp://downloads.netgear.com/files/wg111v2_2_0_0.zip](ftp://downloads.netgear.com/files/wg111v2_2_0_0.zip)

2) Extract files from the zip file using Archive Manager. The file we are interested in is Data1.cab.

3) Install 7zip - available in add/remove software. This allows you to read the above cab file.

4) Open the cab file and extract the contents (again using Archive Manager).

5) Install ndiswrapper if you haven't all ready done so.

6) Amongst the files we extracted from the .cab is a net111v2.inf file. Add this to Windows Wireless Drivers. It may give you an error message about being unable to detect device, but just ignore that.

7) Configure your wireless network connection as normal.

At no point has the blue light on my WG111v2 actually lit up. But I'm online now so it must be working!

Hope that helps.

Luca.

---

### Post by LucaAltieri on 2009-05-23
Update:

It worked for a few hours and now refuses to connect to any wireless networks. It can no longer see the wireless network at home, but it can see my neighbour's - though it can't connect to that either. It tires and fails.

Any ideas?

---

### Post by speed32219 on 2009-05-29
The only way to get that WG111 working in Hardy 8.04 was using ndiswrapper and not well I might add. (Low signal strength).

18 months ago I switched to a trendnet tew-424UB ($25) and still had problems and had to use ndiswrapper with good signal strength.  When I upgraded to it worked right out the box, the drivers were there for the Sis163u chipset  which trendnet uses.

I now have lost the usb 424UB and I am looking for one that is 802.11N/G B compatible and works out the box, I need to check.

To check what is working and available you can go here, not being updated in quite a while.  

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

