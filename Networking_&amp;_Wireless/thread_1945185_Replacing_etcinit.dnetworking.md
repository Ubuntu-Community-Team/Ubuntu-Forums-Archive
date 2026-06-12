---
title: "Replacing /etc/init.d/networking"
date: 2012-03-22
forum: Networking &amp; Wireless
---

### Post by ronni on 2012-03-22
Hi,

I have some Ubuntu virtual machines on a Centos host.

They use different VLANs so the host uses eth0 and the virtual machines needs to use a VLAN-interface, and the eth0 in the virtual machine only needs to be up, but with no ip address.

I couldn't get it to work using iproute2 and the default network configuration, so I created a simple script called network with a start, stop and restart that just executed some scripts in /etc/network where all the iproute2 commands were made.

Then I did a upadte-rc.d network defaults.

It works as it should, the only thing is that when restarting the guest system it stops with "Waiting for network configuration" which takes about 1-2 minutes.

I thought it was the default network configuration scripts, so I tried to remove all content from /etc/network/interfaces which didn't help, so I removed the script from startup using
update-rc.d -f networking remove

This didn't help either, and there still is references in /etc/rcX.d/ for networking.

Does anyone know how to remove all the default network configuration scripts? Or what it is that is waiting for network configuration.

I can't see any references in /etc/rcX.d/ for my network script.

---

