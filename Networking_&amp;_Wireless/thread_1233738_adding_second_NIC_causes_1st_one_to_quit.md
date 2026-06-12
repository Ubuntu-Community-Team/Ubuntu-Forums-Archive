---
title: "adding second NIC causes 1st one to quit"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by computx on 2009-08-07
I have a ubuntu 9.04 server that I use for serving http and a few other things. It is setup to get an address via dhcp and the router is set to give it a dmz address the same as my wan address.
All works quite well. Tonight I had the great idea to setup an ltsp-server on it and as a first step I added a second NIC to the box. I edited  /etc/network/interfaces to set the nic up with a static ip.
My problem is that when I activate both NIC's the one in the DMZ seems to get the correct address but no traffic will go through it. as soon as I deactivate the card with the static IP then the computer starts working as it shoud.
The new NIC is grabbing eth0 and my old card is grabbing eth1. is that the problem and if so is there a way to make them swap to the alternate eth device?
my etc/network/interfaces looks like this
```

iface lo inet loopback

auto eth0
iface eth0 inet dhcp
#iface eth0 inet static
#address 192.168.1.1
#gateway 192.168.1.254
#netmask 192.168.1.255

auto eth1
iface eth1 inet dhcp

```
with the old nic activated by itself route looks like this

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
65.xx.xxx.xxx   *               255.255.255.224 U     0      0        0 eth1
default         adsl-65-xx-xxx- 0.0.0.0         UG    100    0        0 eth1

with both nics

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
65.64.xx.xxx   *               255.255.255.224 U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.254   0.0.0.0         UG    100    0        0 eth0
default         65.64.xx.xxx   0.0.0.0         UG    100    0        0 eth1

Is it possible to reassign the nic to a different eth# and would that help?

---

### Post by Iowan on 2009-08-07
Your */etc/network/interfaces* has both NIC's set for DHCP.
It *might* be possible to edit assignments in */etc/udev/rules.d/70-persistent-net.rules*.

---

### Post by computx on 2009-08-07
Yes I had changed it to dhcp to see what happened but it had previously been set to static via the lines that are now commented out. Regardless of static or DHCP it stops all net traffic. 
In an attempt to bypass the problems I decided to make a different pc the ltsp-server which eliminated the problem. Now I have to figure out why the other pc's aren't finding the server to boot from.

---

