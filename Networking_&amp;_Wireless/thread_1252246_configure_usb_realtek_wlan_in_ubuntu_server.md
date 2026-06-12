---
title: "configure usb realtek wlan in ubuntu server"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by stozi on 2009-08-28
Sorry, I mean Ralink. Not sure where the t in RT73 comes from.

I have Puppy on one partition and my realtek usb wlan works seamlessly in it. I understand the driver should be in the kernel, but Ubuntu Server failed to configure the network on install. I have no cable connection available so getting this working is my only way to get any programs installed.

The network has no wep or wpa. In wicd in xubuntu on my previous install there was no setup, so as I understand it it must by dynamic address.

I added
> auto wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid linksys
wireless-key 

to /etc/network/interfaces. That didn't work.

on boot I see
> [   9.923848] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected
[   9.923928] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.

and a bit later
> configuring network interfaces    [fail]

The chip is RT73(usb)

never mind, got no help so switched to #! Linux.

---

