---
title: "RT3070 Usb Wireless Problems"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by PlasticoBolha on 2012-05-11
Hi guys! ):P)

I'm fairly at Linux, but I'm learning... Please be patient :p


So, I got a problem:

- I got a RT3070 Usb wireless card. When I installed Ubuntu, I could easily find my network (and some more). But when I saw in airmon-ng the devices it appears Wlan0 with unknown chipteset and drivers.

- Then I went to the ralink website, downloaded and installed... (I google it also how to install)
Note: I blacklisted "rt2800usb"

In the airmon-ng it appears:

-------------------------
Interface    Chipset        Driver

ra0        Ralink 2560 PCI    rt2500
-------------------------
(I got a usb not a pci device)

-  My internet is working... But sometimes the connection drops...  And before was flawless. But that was not the problem.


If I dont blacklist the "rt2080usb" it appears:

-------------------------
Interface    Chipset        Driver

wlan0        Ralink RT2870/3070    rt2800usb - [phy0]
-------------------------

Now that's what I was looking for. Right Chipset, right drivers but it doesnt find any networks. The problem that I face is when I try do use the airmon-ng and airodump-ng to... hummm.... test MY internet vulnerability with the "ra0" interface doesnt work. It doesnt appear "mon0" interface altough it says "(monitor mode enabled)" next to "ra0".

With the "wlan0" it works like expected, but with no networks.... 

1) Is it normal?
2) How can I use airmon-ng with these settings?

Help.... 


Thanks in advance! ):P

---

