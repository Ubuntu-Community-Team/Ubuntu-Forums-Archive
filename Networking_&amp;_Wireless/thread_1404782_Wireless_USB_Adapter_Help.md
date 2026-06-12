---
title: "Wireless USB Adapter Help"
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by SquirrelSlax on 2010-02-11
I really need some help with getting a Wireless USB Adapter to work properly.
I'm trying to use a "Realtek Semiconductor Corp RTL8187 Wireless Adapter." (referred to as RT RTL8187) I can get the device to be recognized by the system, but I have to use a "NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]" (which I refer to as NG RTL8187) to do so.

To get the RT RTL8187 to be seen by the system I have to plug the NG RTL8187L into another usb slot while the RT RTL8187 is plugin too. After that both devices can be seen in Terminal using command "lsusb"

```

root@ubuntu:~$ lsusb
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
Bus 001 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Why am I having to do this? And how can I fix this??
The RT RTL8187 is listed as a supported device by ubuntu.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Another Issue I am having is that once the laptop is restarted the RT RTL8187 is no longer recognized/available until I plug the NG RTL8187L in again. 

It seems as though the RT RTL8187 is running off the driver for the NG RTL8187L.
If thats the case, then is there a way to force the RT RTL8187 to use the driver from the NG RTL8187L on boot.

Thank you for any help given.

ISSUE FIXED!

---

### Post by sharke on 2010-02-12
We can try this to get the system to recognise the adaptor without the netgear pluged in.
in a terminal
sudo insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x0bda product=0x8187
Unplug the netgear reeboot past above interminal hit enter then check lsusb and see if recognised.
cheers
sharke

---

### Post by SquirrelSlax on 2010-02-12
Thank you for the response.

The device is not being see on boot.
At least it is listed in the printout when lsusb command is given.
BUT the Network Manager (icon in top right corner) is not seeing/using it. 
After start up (login) the network Icon looks like a computer with an X on it.
I have to unplug the RT RTL8187, then plug it back in before its being see by the network manager. then the icon changes to the WiFi signal bars

How would I get the network manager to see it.

---

### Post by sharke on 2010-02-12
I must be getting old i had your adaptor confused with a usb modem.
after reboot with only the one adaptor.
 in a terminal sudo modprobe rtl8187
Regards
Sharke

---

### Post by SquirrelSlax on 2010-02-12
Sorry I meant to say, the RealTek RTL8187 is listed under lsusb, after reboot
but the Network Manager is not seeing it or using it until the NetGear is plugged in.

Do i need to paste 
sudo insmod /lib/modules/`uname -r`/kernel/\
drivers/usb/serial/usbserial.ko \
vendor=0x0bda product=0x8187 
into the  /etc/rc.local file?

---

### Post by SquirrelSlax on 2010-02-12
I pasted that code in the file,
and now my linux system wont start. It hangs on load screen

Got system to boot,
and got adapter to work another way.
Thanks for help though

---

