---
title: "ZEW 2500p, loaded rt2800usb module, doesn't work"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by Xenphor on 2010-05-21
I'm running Xubuntu 10.04; I have a Zonet wireless usb card (ZEW2500P). I'm still not sure exactly which ralink chipset it is using. This page [http://ralink.rapla.net/](http://ralink.rapla.net/) has it listed as a RT2500 device. According to the tutorial I was reading on rt2500 devices, the card should already work. However, when I do a nm-tool, I get this for the non-working device:

Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        00:A1:B0:C0:52:B1

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

It should be noted that I also have an Intel Pro Wirless device that IS working on the computer. It seems to me that Ubuntu is using that as its default device. I would instead like to use my USB Ralink.

Is the rt2800usb Driver the correct one for this supposed rt2500 based device? If so, is there a way that I could easily switch between the two if both cannot be up at the same time? Thanks.

---

