---
title: "Ubuntu 10.04 Asus USB-N13 not managed by network manager"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by nuclear_sunshine on 2010-10-03
Hi,
Just purchased a Asus USB-N13, and having follwed a mixture of tutorials, including the readme on the driver disk, i have had no luck in getting this adapter to work.

Upon using "sudo iwlist ra0 scan" the adapter can see multiple networks, however device manager is stating that the device is not managed. How can I get this sorted and connect to a network?

Will post lsusb and iwconfig below.

lsusb


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 002 Device 005: ID 0b05:1784 ASUSTek Computer, Inc.   << this is the adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig


lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2870 Wireless  ESSID:"<home-network>"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:1D:68:00:1D:CF   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-61 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

usb0      no wireless extensions.

Many thanks.

---

### Post by nuclear_sunshine on 2010-10-03
tiny bump

---

