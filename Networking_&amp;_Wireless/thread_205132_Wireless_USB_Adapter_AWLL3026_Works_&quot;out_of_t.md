---
title: "Wireless USB Adapter AWLL3026 Works &quot;out of the box&quot;"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by ralo503 on 2006-06-28
Works fine on Dapper 6.06


USB Adapter AWLL3026 Works "out of the box"   :)

---

### Post by GLMontyWV on 2006-10-28
Anyone getting this to work on Edgy?  Have this one and an Airlink AWLH3026 and can't get either one to work.  Complete less that 24hr noob here.  Appreciate any help.

Thanks, Monty

---

### Post by GLMontyWV on 2006-10-30
Can someone explain the process for getting this to work "out of the box" with Dapper? Totally noob here.  Thanks!

Monty

---

### Post by GLMontyWV on 2006-12-22
FYI - if you are wanting to use this device and you want Edgy, Linux Mint 2.1 works out of the box with this usb wifi device.

Monty

---

### Post by stoshb on 2007-02-04
I too am unable to get this to work.  I have a brand new install of 6.10 on a Dell 4300.  

In device manager I see the interface.  

lsusb sees the device

Last thing tried was to download some new firmware drivers and this did not help.

Never see wlan0 when I try iwconfig.

In Iwconfig all I do see eth1 (there is a network card for wired access in box but no wire to the router which is why this is not on eth0).  When I see it I have even gotten as far as seeing the mac address of the interface.

Do also see good signal strength from wireless router.  Am accessing this router, from another computer in the same room as I write.

Never get an IP from DHCP, can do nothing if I "hard-code" the IP address.  

Am worried that there may be some issue with WEP but am not certain.  

Any other suggestions?

---

### Post by truelifestudio on 2007-03-02
Stosh,

We are having the same issues.  Ok I can connect to the router, but am unable to pull an IP.  

Below is a list of things that I have tried:

1) Network-manager
2) WPA
3) Now using open WEP
4) No Encryption
5) Compiled my own drivers (This resulted in the Eth1 card becoming wlan0) Still nothing else.

What really annoys me is the card works.  I can change essid / modes.  Why won't iwconfig work?  Every program I use depends on it.

Help...

---

