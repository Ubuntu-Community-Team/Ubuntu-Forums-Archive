---
title: "Wireless stepby step guidence needed."
date: 2006-05-30
forum: Networking &amp; Wireless
---

### Post by TAEAS on 2006-05-30
Hello is there anybody out there?

I have a 3Com USB wireless dongle 3crusb10075 & i have downloaded the linux driver on the site.
But i am having problems loading this driver.
I cant get access to wlan0 in Networking.
> tae@TAE:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.


> sudo lshw -businfo
usb@4:5                generic     3CRUSB10075

pci@00:12.0  eth0      network     VT6102 [Rhine-II]
             wlan0     network     Ethernet interface



Need help on how to activate the network?
sudo lshw
*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:cb:c0:c0:51
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


Hopefully there will be someone to guide me into a safe harbour?
What do i need to do, have tried ndiswrapper but no luck,](*,)

---

### Post by jml on 2006-05-30
Here is the Ubuntu Wireless Troubleshooting guide.  Hope it will be of help.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe

---

### Post by TAEAS on 2006-05-31
[QUOTE=jml]Here is the Ubuntu Wireless Troubleshooting guide.  Hope it will be of help.

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Joe[/QUOTE]


Thanks Joe, but i have already gone up & down that list, so probarly i am doing something wrong.:confused:

---

### Post by TAEAS on 2006-05-31
[QUOTE=TAEAS]Thanks Joe, but i have already gone up & down that list, so probarly i am doing something wrong.:confused:[/QUOTE]


So i hope there is somebody who can try to guide me, & help me see the light.

---

