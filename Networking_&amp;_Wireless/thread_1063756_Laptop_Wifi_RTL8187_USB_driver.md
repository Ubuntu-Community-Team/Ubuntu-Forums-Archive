---
title: "Laptop Wifi RTL8187 USB driver"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by ambidextrousone on 2009-02-08
sadly, i dont have a wireless connection availiable right here, nearest place is mcdonalds ;)

i used that command, but its only showing me the details of the ethernet, annoyingly, it isnt being quite as detailed for the wireless device, what are we looking for?

---

### Post by ugm6hr on 2009-02-08
> **ambidextrousone said:**
> it isnt being quite as detailed for the wireless device, what are we looking for?

Details of chipset and driver.

Maybe try finding it in (depending on PCI or USB):
```
lspci
lsusb
```

lshw should still find it... not sure why it doesn't, unless it is not even recognised as a networking device (which would spell trouble).

---

### Post by ambidextrousone on 2009-02-08
ill try and grab the part from your original command you gave me, that seems to show wireless details.

description : wireless interface
physical id : 1
logical name : wlan0
serial 00:15:af:11:5f:1d
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

im not sure if the thernet device also controls the wireless, but the name of that device is :

RTL8111/8168B PCI Express Gigabit Ethernet controller

im doing all this through live cd, i can check it out through windows.. grudgingly ;) would rather do it the linux way so i know a little more about what im doing heh

---

### Post by ugm6hr on 2009-02-08
So no driver auto-loaded....

**lspci** should give a list that includes the hardware chipset.

PS: Is it OK if I divide this thread and move this new wifi discussion to the Networking sub-forum?

---

### Post by ambidextrousone on 2009-02-08
lspci is showing all the devices from usb, to pci bridges, only one ethernet controller here which is that realtek semiconductor co one i put in my last post =) its ok if its non compatible, she will be plugging into a cable at home anyway

bare in mind, its the mint live cd im still using atm, buntu might have a much bigger population of preloaded wireless network drivers

---

### Post by ambidextrousone on 2009-02-08
of course, your the mod here :) get us moved :)

---

### Post by ambidextrousone on 2009-02-08
thank you for moving us over ugm6hr.

i still have an option to booting up windoze and find out once and for all what wireless this thing has?

---

### Post by ugm6hr on 2009-02-08
I know some bargain-basement laptops have internal USB wifi devices (I know - seems pointless).

Post output (i.e. copy & paste) from *lsusb*

It must appear in either lspci or lsusb, since it is recognised by lshw as a network device (and given wlan0 as id).

USB wifi devices are generally slightly trickier to install in Linux.  I have only ever installed 2 (1 surprisingly worked out-of-the-box with Hardy and 1 needed the serialmonkey drivers).

---

### Post by ambidextrousone on 2009-02-08
in order to save us some time, i did boot windows xp - which took AGES, cant wait to scrap it!!!

you are right, usb

realtek RTL8187 wireless 802.11g 54mbps USB 2.0 network adapter

its worse than i thought -_- im just downloading 8.04 since im feeling a little more convinced that will run run more smoothly, can go back into mint for now if you like?

btw, went back into mint and run lsusb, which did recognise the wireless device, the other devices are all linux foundation root hubs

would copy/paste - im talking to you from my trusty buntu, spinning over to the laptop when needed :)

---

### Post by ugm6hr on 2009-02-08
As long as it is a genuine rtl8187 (not 8187b) device - it should (theoretically) work out-of-the-box with Ubuntu.

Unfortunately, no way to try it out without a nearby wifi access point.

The output from lsusb would still be helpful to confirm.

---

### Post by ambidextrousone on 2009-02-08
Bus 005 Device 002: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 005 Device 001 ID 1d6b: 0002 Linux Foundation 2.0 root hub
Bus 004 Device 001 ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 003 Device 001 ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 002 Device 001 ID 1d6b: 0001 Linux Foundation 1.1 root hub
Bus 001 Device 001 ID 1d6b: 0001 Linux Foundation 1.1 root hub

---

### Post by ugm6hr on 2009-02-08
Some refertences which may prove useful:
[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)
[http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/](http://globalsyzygy.wordpress.com/2007/12/30/fixing-your-rtl8187-netgear-wg111v2-in-ubuntu/)
[http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/](http://www.datanorth.net/~cuervo/blog/rtl8187b-drivers-and-patches/)

#EDIT:
OK. Seen your lsusb - looks promising.
[http://ubuntuforums.org/showthread.php?p=5090337](http://ubuntuforums.org/showthread.php?p=5090337)
[https://answers.launchpad.net/ubuntu/+question/31734](https://answers.launchpad.net/ubuntu/+question/31734)

It should work out-of-the-box - but if it doesn't, it shouldn't be too hard to fix

---

### Post by ambidextrousone on 2009-02-08
fantastic, ill be getting that sorted tonight when 8.04 has burned :) thanks for putting up with me ugm6hr!

ill come and harass ya through message if i get really lost ;) lol

-ambi out

---

