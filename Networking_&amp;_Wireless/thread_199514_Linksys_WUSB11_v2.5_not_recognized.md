---
title: "Linksys WUSB11 v2.5 not recognized"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by booyabazooka on 2006-06-18
Trying to use USB for a network interface, I know, is a terribly obnoxious idea, but it's the hardware I have.  I've plugged in the card, and rebooted, and it isn't listed in Device Manager.

I suppose I have a pci wireless nic that I could salvage from another machine, but I'm hoping it doesn't have to come to that yet.  Any ideas?

---

### Post by booyabazooka on 2006-06-19
Alright, so... for some reason, unplugging the device and plugging it in again did the trick, as far as getting Ubuntu to at least see it.  But it's still not being recognized as a network interface.

Linksys apparently has [drivers]("http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1121874580756&pagename=Linksys%2FCommon%2FVisitorWrapper") available for this card.  But, may I ask, why does neither the linux source nor a compiler come with an Ubuntu installation?  Do Ubuntu users never feel the need to install anything?

---

### Post by booyabazooka on 2006-06-19
More update: I've installed the package [linux-wlan-ng]("http://packages.ubuntu.com/dapper/admin/linux-wlan-ng").  So, supposedly I have the necessary drivers installed.  Still, Ubuntu seems to be making no effort to use this device.  Where do I need to go to troubleshoot it?  Any clue whatsoever where to look to see what this device is doing, or why Ubuntu doesn't even seem to know that it's a network interface?

---

### Post by az on 2006-06-19
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearMA111)

---

### Post by booyabazooka on 2006-06-19
As far as I can tell, I have followed every instruction, and everything has installed properly.  The only thing that's not happening: The wireless interface wlan0... doesn't seem to exist.

lsmod | grep prism
```
prism2_usb       77060  0
usbcore         129668  6  prism2_usb,usbhid,uhci_hcd
```

sudo apt-get install linux-wlan-ng
. . .
```
linux-wlan-ng is already the newest version
```

sudo gedit /etc/modprobe.d/wlan
file contents:
```
alias wlan0 prism2_usb
```

sudo gedit /etc/network/interfaces
file contents:
. . . 
```
auto wlan0
iface wlan0 inet dhcp
    wireless_mode managed
    wireless_essid linksys
```

sudo ifup wlan0
```
ifup: interface wlan0 already configured
```

ifconfig wlan0
```
wlan0    Link encap:Ethernet  HWaddr 00:00:00:00:00:00
```

iwconfig wlan0
```
wlan0    no wireless extensions
```

---

### Post by az on 2006-06-20
[QUOTE=booyabazooka]
sudo ifup wlan0
```
ifup: interface wlan0 already configured
```
[/QUOTE]


Try unplugging and the replugging the device.  I have had to do this maybe three times to get the device to work.  After that, it seems to work forever.

If this does not work, maybe you have a firmware problem?  There is a linux-wlan firmware package which fetches the latest firmware for your device.  I never have had to use it.  You need to be on the net to get it to download the firmware.... (catch-22, maybe?)

---

