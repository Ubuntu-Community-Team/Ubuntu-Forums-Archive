---
title: "New to Ubuntu- Can't get networking to work"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by MidnightJava on 2011-06-12
I've been developing software on Linux (RHEL) for a couple years, but I'm new to Ubuntu. I was impressed that it only took me 10 min to install it, but I've spent hours trying to get Ubuntu to connect my system to the Internet, a connection that was working fine under Windows.

My wireless driver isn't supported by Linix, but I found instructions on-line for modifying and re-compiling the driver. I need to be connected to the Internet to download the driver and some package dependencies for building it. The Linux box is nowhere near my Internet connection, so I brought my Macbook Pro down to it, using it's wireless card to connect to the Internet, with an Ethernet Cable between the Linux box and the MBP.

I'm using separate subnets for the wired and wireless connections, as follows:

Linux: 192.168.2.170, gateway 192.168.2.175

MBP wired port: 192.168.2.175, gateway 192.168.1.1

MBP wireless port: 192.168.1.5, gateway 192.168.1.1

Verizon Fios router: 192.168.1.1

The MBP is configured to share its wireless Internet connection to computers on the wired port.

I configured the Linux IP settings by editing /etc/network/interfaces and then running sudo /etc/init.d/networking start. (I tried configuring it using the GUI by selecting "Edit Connections" from the network status icon, but whatever I set here doesn't seem to be reflected when I run ifconfig.)

ifconfig shows the network is configured as expected. I get connectivity to the Internet for about a minute or so, and then it goes down. It also causes the MBP to lose its Internet connection at that point. If I unplug the Ethernet cable to the Linux box, the MBP connects right away to the Internet. If I plug the cable back in and stop and start Linux networking, I get a minute or so of connectivity again, then I lose it again.

It sorta behaves like an IP address conflict; but I'm using separate subnets, and it seems to fail at the same time, as if something is timing out. I can bring the Linux box upstairs to where the Internet connection is and see if it works directly connected; but it seems this setup should work, and I'd like to know why it's not.

I'm running Ubuntu 11.04 on an HP Pavilion 64-bit dual core system.

---

### Post by MidnightJava on 2011-06-14
The problem was with the Mac. I had the Mac and the Linux box using static IP addresses on the wired connection. I switched to dynamic addressing, and that solved the problem. However, on the Mac I had to select "Using DHCP with Manual Address" to get it to work. When I selected "Using DHCP" I got the same behavior that I saw with static addresses.

---

