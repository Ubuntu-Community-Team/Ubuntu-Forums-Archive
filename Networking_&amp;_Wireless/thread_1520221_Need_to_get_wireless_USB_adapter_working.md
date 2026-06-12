---
title: "Need to get wireless USB adapter working"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by blueridgedog on 2010-06-29
I use Ubuntu full time on my desktop.  I have had to move and will need to use a USB wireless adapter due to the location of my new office.

I bought two, assuming one would work.

The first:
lsusb shows 1737:0075 linksys
It is actually a WUSB54GSC V2
Upon install nothing happens.  Google indicates that is is a broadcom chipset, BCM4320

The Second:
lsusb shows 148f:2770 ralink technology Corp
It is branded as a Rosewill RNX-N100
Upon installing this card, it is recognized as a wireless adapter and can connect, but using ping to test the connection to the router results in many dropped packets and the connection eventually drops.

Can either of these be made to work?  I am encouraged by the Ralink unit, as it is recognized at least.

I can download .deb files here at work and take them home if there are items I need to install.

If not, what should I order? I have a few days before DSL will be installed and can order another adapter if there is one that is recommended (a link to a newegg product would be great).

---

### Post by ieee488 on 2010-06-29
there is a list of supported wireless devices so you didn't have to guess
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by okplayer02 on 2010-06-29
> **blueridgedog said:**
> I use Ubuntu full time on my desktop.  I have had to move and will need to use a USB wireless adapter due to the location of my new office.

I bought two, assuming one would work.

The first:
lsusb shows 1737:0075 linksys
It is actually a WUSB54GSC V2
Upon install nothing happens.  Google indicates that is is a broadcom chipset, BCM4320

The Second:
lsusb shows 148f:2770 ralink technology Corp
It is branded as a Rosewill RNX-N100
Upon installing this card, it is recognized as a wireless adapter and can connect, but using ping to test the connection to the router results in many dropped packets and the connection eventually drops.

Can either of these be made to work?  I am encouraged by the Ralink unit, as it is recognized at least.

I can download .deb files here at work and take them home if there are items I need to install.

If not, what should I order? I have a few days before DSL will be installed and can order another adapter if there is one that is recommended (a link to a newegg product would be great).


after you plug the usb stick in run the command 


```
dmesg | tail
```

this will show if the firmware has been loaded for ur usb stick 
that list may or may not be up to date this will for sure tell you what is happening.

---

