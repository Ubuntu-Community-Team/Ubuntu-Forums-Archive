---
title: "Installing Netgear Wg111v2"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by Dsky on 2010-10-20
Hi everyone,

im on xubuntu and im trying to install my wirlesskey wg111v2.

when i plug in the key i see it in the network manager but it says me "connection disabled"

what can it be?

---

### Post by Dsky on 2010-10-21
and its impossible to click on "enable wireless" (i dont know how ubuntu traduce it in english)

---

### Post by Dsky on 2010-10-22
up...

---

### Post by Dsky on 2010-10-24
up

---

### Post by Dsky on 2010-10-26
up

---

### Post by fizyxnrd on 2010-10-28
I'm having a similar problem.  I am using a Netgear WG111v2 USB wireless dongle.  I've been using it with zero problems under 9.04 and 9.10 for months.  I just upgraded to 10.04, and I lost my wireless capability.

The device shows up with lsusb
```
Bus 001 Device 004: ID 0846:4240 NetGear, Inc. WG111(v1) rev 2 54 Mbps Wireless [Intersil ISL3887]
```
but I can't get any kind of interface based on it.

iwconfig only returns the local and wired interface:
```
lo        no wireless extensions.

eth1      no wireless extensions.

```
The interface used to be wlan0, but trying to force the interface into existence hasn't worked yet.

Lucid did recognize an ancient D-Link (DWL-122) USB wireless dongle I plugged in, but unfortunately, this one doesn't support WPA, so I can't use it.

Does anyone know what the issue preventing Lucid from playing nice with the RTL8187 driver is?  (Or is this actually the problem?)

---

### Post by fizyxnrd on 2010-10-28
What worked for me was installing the linux-firmware-nonfree package, as explained in
[this thread]("http://ubuntuforums.org/showthread.php?t=1594592&highlight=netgear+wg111").

---

