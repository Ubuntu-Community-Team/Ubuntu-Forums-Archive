---
title: "Trouble with simultaneous Ethernet for LAN and Ethernet for IP Camera"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by dsurfer21 on 2012-10-17
Hello,

I am running ubuntu 12.04.  I have a desktop that has two ethernet cards.  I would like to use one ethernet port (eth 1) for SSH connections or connecting to a LAN to access the internet.  The other ethernet port is to use an ethernet IP camera.

I am having an issue where I can use SSH or the LAN on eth1 when I have the camera disconnected from eth0.  I can also use the camera on eth0 only when I am disconnected on eth1.

How can I run them simultaneously?

I am not very knowledgeable with networking but the /etc/network/interfaces is setup like:
[FONT=monospace]
[/FONT]    auto eth0     
iface eth0 inet static         
address 192.168.0.92         
netmask 255.255.255.0         
gateway 192.168.0.254
    
auto eth1     
iface eth0 inet static         
address 192.168.0.77         
netmask 255.255.255.0         
gateway 192.168.0.254


The IP address of the camera is 192.168.0.90.  I'm not sure how to set up the gateways.  Could that be the problem? I would like to use static IP addresses. When I run ifconfig eth0 and eth1 show up properly with the ip addresses that I specified above.

I'm hoping there is a solution.  I modified the grub file so that I can boot up right into a terminal.  I then use sudo service lightdm when I want to run ubuntu desktop.  I'm hoping I can use both ethernet ports simultaneously right at the command prompt when it boots up, and also when I start ubuntu desktop.

Thanks.

---

### Post by jingaling on 2012-10-18
I think the problem is caused by the fact that both interfaces are on the same subnet.

Try changing the subnet on the camera NIC (eth0?). Your system may be getting confused and not routing the packets down the right NIC correctly. If it was me, I would have it setup like this:

Main NIC (used for SSH and internet)
IP - 192.168.0.X
Subnet - 255.255.255.0
Gateway - The IP address of your router (192.168.0.254 by the looks of things).

Camera NIC
IP - 10.0.0.X
Subnet - 255.255.255.0
Gateway - 127.0.0.1 (this is a loop back address that tells the machine that itself is the gateway)

Camera IP details will be the same as above with the last octet in the IP address being different from the second NIC in your machine.

This may not work as it's completely none standard. You may need to have a second routing device on the 10 range network to maintain and ARP table etc so that routing will work.

Why don't you just plug your camera directly into your router? This will vastly simplify the network and allow you to use both at the same time.

---

### Post by dsurfer21 on 2012-10-18
Hi Jingaling,
I appreciate your response.

Basically there is no router.  I have a desktop that has an IP camera directly connected to eth0.  I have eth1 available for SSH connections with other devices such as embedded processors that I am using for some field testing.

I would like to keep the IP camera settings as they are.  It has an IP address of 192.168.0.90.  

I would like to use the IP address of 192.168.0.78 for SSH connections.  This one I can change if necessary.

Any ideas what I should try?

---

### Post by jingaling on 2012-10-18
As I said, you should try changing the subnet on one of the NIC's. If you must keep the IP of the camera then change the subnet of the other NIC.

If you don't have a router then how is your traffic being routed? What does your gateway address correspond to then?

The easiest way to achieve your aim is to have a router then have all of your device plug into that. This will enable you to SSH and contact your IP camera at the same time using only one NIC.

---

