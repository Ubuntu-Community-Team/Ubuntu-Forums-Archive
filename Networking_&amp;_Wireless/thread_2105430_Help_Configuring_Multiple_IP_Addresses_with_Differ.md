---
title: "Help Configuring Multiple IP Addresses with Different Gateways in Interfaces"
date: 2013-01-16
forum: Networking &amp; Wireless
---

### Post by own3mall on 2013-01-16
Hi All,

I'm trying to setup 15 or so different IP addresses that I'd like the eth0 interface to bind on.  I've looked online at quite a few guides that show how to add multiple IP addresses to the /etc/network/interfaces file.  However, they do not show a configuration in which different ranges of IP addresses are added on one interface.  So, based on what I found, I have the following (the IP Addresses have been randomized for privacy, so of course the IPs themselves don't look right):

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 74.3.3.2
netmask 255.255.255.248
network 74.3.3.1
broadcast 74.3.3.3
gateway 74.3.3.4

auto eth0:0
iface eth0:0 inet static
address 77.1.1.100
netmask 255.255.255.252
gateway 77.1.1.92

auto eth0:1
{etc...}
{goes up to auto eth0:13}

```Does this look right?  Is there an easier / better way to do this?

Do the settings in the interfaces and the networking daemon run by default in Ubuntu with XWindows installed?

```

sudo update-rc.d networking defaults

```Would this code make sure the networking daemon is running by default when the computer starts?  Would network manager in gnome still work for other devices besides what is configured in the interfaces file?

Any help is appreciated.  Thanks!

---

### Post by chadk5utc on 2013-01-16
Have a look here 
[http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html)

---

### Post by own3mall on 2013-01-16
> **chadk5utc said:**
> Have a look here 
[http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html)

I guess that means I have it setup correctly?

---

