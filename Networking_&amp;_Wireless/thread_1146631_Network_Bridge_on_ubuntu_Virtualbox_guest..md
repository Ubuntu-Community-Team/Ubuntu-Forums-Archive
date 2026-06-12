---
title: "Network Bridge on ubuntu Virtualbox guest."
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by A.Exell on 2009-05-02
Ok, I'm new to the whole Linux experience but decided I had to try my hand!  Now I don't have a machine I can mess around with dual boot on at the moment, so I use Sun's Virtual box  VM.  So I have a an ubuntu 8.10 guest on a vista 64 host and most things work fine.  However....

I'm attempting to establish a network bridge on the guest ubuntu between eth0 and and tap0  (tap0 is a virtual vpn adapter created using Openvpn).  In order to test the VPN I'm trying to establish, I have the VirtualBox network connection configured as NAT.

On startup I have a eth0 network connection on 10.0.2.15 and can see out past the VirtualBox NAT.  However everytime I establish the bridge I lose all network connection.  The bridge is configured to use the same settings as initially present on eth0 (IP, NetMask and Broadcast) using "ifconfig" and as far as I can tell should work.   I'm using the basic bridge scripts from Openvpn which use "brctl" to create the bridge.  I can see the bridge is present if I "ifconfig" and I can ping 10.0.0.2 and 10.0.0.3 which appear to be related to the VirtualBox gateway.  However all other traffic in and out appears dead and nothing is routed in or out, I.E. no web access and requests to the VPN port from outside the NAT fail. If I don't start the bridge these all work fine.

Has anyone else out there tried this and can you shed some light on the subject?  I'm obviously missing something but I just can't see it!

Hope someone can help!

---

