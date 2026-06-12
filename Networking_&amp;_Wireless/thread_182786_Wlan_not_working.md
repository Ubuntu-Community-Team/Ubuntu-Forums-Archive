---
title: "Wlan not working"
date: 2006-05-26
forum: Networking &amp; Wireless
---

### Post by ubuntunewbie on 2006-05-26
I have installed kubuntu (breezy) on my sony vaio.
i have a netgear ma111 usb adapter and am trying to configure my wireless connection to work with kubuntu
i followed exactly all instructions mentioned at this link
[https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111](https://wiki.ubuntu.com/WifiDocs/Device/NetgearMA111)

but the wlan is still not working. 

here are some details of what i did

1. /etc/modprobe.conf did not exist with original installation. i created it to add the alias statement

2. i added the following statements at the end of /etc/network/interfaces (abcnet is my essid)

iface wlan0 inet dhcp # if you want dhcp for wireless
auto wlan0 #comment if you don't want it boot at start
wireless_mode managed
wireless_essid abcnet
i have disabled encryption for now and so, did not add the encryption related stuff.

When i did sudo ifup wlan0, it says misplaced option and gives line number of the statement - wireless_mode managed

i checked the network interfaces and the system does detect my MA111 wireless usb adapter ( there is an entry out there for it).

Can somebody please help???? I can provide additional details if required.
__________________

---

### Post by chrisharte on 2006-05-28
Hi,

I finally successfully installed my MA111 on Ubuntu breezy yesterday - it took a long time because it didn't want to work at first. The problem on my machine seemed to be that the MA111 device was recognised automatically by breezy as a prism2_usb driver device.  For whatever reason that driver doesn't actually work properly with the MA111 anymore (although the wiki page about the MA111 says that it should work with it...) so you have to use ndiswrapper. Also - and crucial to the number of hours I took getting it running - it will conflict with ndiswrapper if you don't unload the prism module first. 

I used the ndiswrapper to install the WinXP driver off the original netgear CD:

$sudo ndiswrapper -i NETMA111.INF

Unload the prism2_usb (it conflicts in some way with the ndiswrapper):

$sudo modprobe -r prism2_usb

then load the ndiswrapper in its place:

$sudo depmod -a
$sudo modprobe ndiswrapper

After that it should just be a case of telling the device what it should be doing:

$sudo iwconfig wlan0 essid MyEssid
$sudo iwconfig wlan0 mode mymode
$sudo iwconfig wlan0 key xxxmykeyxxxxxx
$sudo ifdown wlan0
$sudo ifup wlan0 

then hopefully Bob's your uncle... 

For more info on ndiswrapper see the wiki page with all the instructions:
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

Chris

---

### Post by tormod on 2006-06-17
[QUOTE=ubuntunewbie]When i did sudo ifup wlan0, it says misplaced option and gives line number of the statement - wireless_mode managed[/QUOTE]

The ordering of the lines in /etc/network/interfaces was a little strange on that wiki page (I have fixed it now I think).

I have put together some up-to-date information about the prism2_usb drivers on [https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb](https://wiki.ubuntu.com/WifiDocs/Driver/prism2_usb)

---

