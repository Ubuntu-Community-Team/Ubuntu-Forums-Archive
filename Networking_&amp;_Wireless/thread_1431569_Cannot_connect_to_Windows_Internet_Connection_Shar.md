---
title: "Cannot connect to Windows Internet Connection Share (ICS)"
date: 2010-03-16
forum: Networking &amp; Wireless
---

### Post by discord on 2010-03-16
Hello,

My friend is trying to share his clearwire connection with me using Windows ICS. Using network-manager or wicd, I am unable to connect to his share. I am able to connect unencrypted with iwconfig, to the ad-hoc network, and then use dhclient to gain ip address. I am not able to connect to WPA encrypted share using network-manager or wicd. nm-applet crashes when trying to connect. I am attempting to setup wpa_supplicant, but haven't got it working yet.

As usual, the wireless networking out of the box experience in Ubuntu doesn't work. This is extremely frustrating. If Ubunut's goals are to be the default desktop, then these guys need to get wifi that "Just Works"...

---

### Post by gordintoronto on 2010-03-16
Wifi "just works" with supported hardware.  It took me longer to set up the wireless on this computer with a D-Link DWL-G510 under Windows 7 than under Ubuntu.

It's harder if you don't know the language, for example, you use WICD or Network Manager to connect to an "access point," not a "share."

What version of Ubuntu are you using? What wireless hardware? (lsusb or lspci)? When you tried with Network Manager, exactly what action did you perform, and what was the result?

---

### Post by discord on 2010-03-17
I'm not a windows fan, I used debian before ubuntu existed. just thought I'd make that clear to you. anyhow my hardware is supported. I'm using the intel iwl3945 driver. Go ahead, create a network in windows7. furthermore, connect a dsl router, or clearwire usb, etc to the windows 7 machine. turn on internet connection sharing, set a wep or wpa password. you will not be able to connect. for some reason network-manager and wicd cannot handle the ad-hoc connection. I am able to connect with no encryption using iwconfig, but this is not wireless that "Just Works"

---

### Post by discord on 2010-03-23
Bump!

---

