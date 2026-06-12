---
title: "Virtual routing through IPS device"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by aviatrd on 2012-02-10
I have a virtual team in VMware Workstation running on my native Ubuntu box.  The purpose of my virtual network is to test IPS signatures in an isolated,  controlled environment.  In my virtual environment are the following vm's:
 
1 Backtrack5 box for network monitoring and simulation
1 Ubuntu 10.04 box for interacting with the web interface of my IPS device and sending it traffic
1 IPS device image
1 other monitoring device
 
All devices are on the same subnet in 192.168.0.0/24, and can fully communicate with each other on vmnet1, where all virtual interfaces are connected.
 
How can I forward the traffic through the IPS device?  I need to be able to send sample traffic from the Ubuntu box through the IPS device, but obviously once it leaves the box, it heads straight for the virtual switch or router.  I am using tcpreplay to simulate an http session, sending one side of the conversation out eth1 and the replies out eth2 on the Ubuntu box, reserving eth0 for standard communications.  Due to the nature of the IPS, one interface has an IP address but the two that sniff traffic are transparent and do not have addresses.  In a physical environment it would be a simple case of plugging it in.
 
I'm stumped on this one.  Any ideas?  Is there an easy solution with iptables that I'm missing?

---

