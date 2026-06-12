---
title: "Dell 1520 Ethernet Wired connection"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by JonPi on 2011-02-02
I have looked over the forums but can't find one word about hard wired ethernet.

Kubuntu 10.04.1 installed on Dell 1520, Broadcom BCM43xx Chipset abg
wireless, don't know the ethernet interface. I'm not concerned with the
wireless; I can get that working if I have ethernet port connection.

Does not recognise ethernet cable connection to router via ping 192.168.0.1

ifconfig eth0 shows "error fetching interfact information: device not found"

ifconfig -a shows lo and wlan0

I want to get the ethernet cable to function so I can get the wireless working
but need the driver. At this point I can't connect to anything. It appears the
ethernet connection doesn't exist eventhough there is a port with a cable to
the router & verified active???

How do I get the ethernet port working.

Blessings,
Jon

---

### Post by dineshs on 2011-02-03
> ifconfig -a shows lo and wlan0Did you try ```
sudo lshw -C network
```
Hope enable networking is ticked when you rightclick (K)Network manager icon .

---

### Post by JonPi on 2011-02-03
Thanks dineshs,
I did try: sudo lshw -C network

I also tried:
ifconfig eth0
ifconfig -a
iwconfig
lsusb
lshw - html >> lshw.html
None show eth0 -- except they can't find it!  I have swaped cables with another computer that is connected -- it also run Kubuntu 10.04

I thought I knew Lenix pretty well after using it for 12 years but this stumps me.

Blessings,

Jon

---

### Post by grahammechanical on 2011-02-03
My motherboard BIOS has a function that allows me to enable or disable the onboard PCIe LAN or the PCI Lan, which are represented as eth0 and eth1. Could your ethernet LAN be disabled in the BIOS?

Regards.

---

