---
title: "Connect Ubuntu server 9.04 to WPA2 encripted wifi network?"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by ADGC on 2009-10-18
I have a system running Ubuntu server 9.04 that I'd like to use as a wireless bridge.  The wifi adapter that's connected to this system is a Rosewill RNX-N2X, which Ubuntu recognizes as ra0 (the device is an usb adapter).  

My question is, how do I configure the /etc/network/interfaces file so that I can connect my system running Ubuntu server to a WPA2-PSK secured network using AES encryption?

For what it is worth, I've so far added the following lines to the /etc/network/interfaces file:

auto ra0
iface ra0 inet dhcp
    wireless-mode master
    wireless-essid "<network name>"
    wireless-channel 1
    #wireless-key <key>

---

