---
title: "Multi Homed local / internet setup"
date: 2010-11-23
forum: Networking &amp; Wireless
---

### Post by TC!! on 2010-11-23
I've got a Ubuntu box with two network cards, the box is running motion to capture images from my ip security camera. I've realised that the traffic from this camera is swamping my network so I'd like to make my ubuntu box multihomed and have the ip camera connected directly to the ubuntu box.

I've tried setting this up using this /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto eth0
        iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        gateway 192.168.1.1

auto eth1
        iface eth1 inet static
        address 192.168.2.5
        netmask 255.255.255.0
        gateway 192.168.2.1

eth1 is the one connected directly to the camera and the camera has an ip address of 192.168.2.55

My problem is that I can ping and ssh to the ubuntu box at 192.1681.5 but it won't connect to the internet. It looks like the traffic is trying to use the 192.168.2.1 gateway which doesn't exist. 

I fixed it using this:
ip route add default via 192.168.1.1

But now I have to type that in after ever restart, how do I make this setting stick?

---

### Post by SeijiSensei on 2010-11-23
Remove the "gateway" directive for eth1.

---

### Post by pricetech on 2010-11-23
Yes, remove the Gateway entry from your ETH1.  More than one gateway entry, even if both exist, creates problems with access outside the subnet.

---

### Post by TC!! on 2010-12-09
Thanks for the replies, that fixed it for me.

---

