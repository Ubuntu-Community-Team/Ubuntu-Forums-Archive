---
title: "Network/Apache2/Firewall problems"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by Vertigo_ on 2010-03-02
Ok, I'm not sure where the problem lies... so any guidance will be much appreciated.

The setup is this: I have two firewalls/gateways, one(Untangle) manages the network and VPN, the other(Smoothie 3.0) was from before I started using untangle and just handles some port forwards. I have a Ubuntu 9.10 box running Apache2 and hosting my VM's. The Smoothie forwards port 80 to the webserver, which is set to a static IP and uses the smoothie as it's gateway.

The problem is when I plug in my second NIC to the network to pickup DHCP the webserver is no longer visible from the Internet. Apache is still running, and if I type in the local address shows up, but it stops responding to the port forward. The second card is set to DHCP so that computers can see the webserver over the VPN. 

Perhaps this is a convoluted setup, I'll admit to that, but for the time it's what I need. Any ideas whats going on? Do I need to set Eth1 to the default?

Firewall One(Untangle):
External: 98.214.xxx.xx1
Internal: 10.1.0.1 / 16
------------------------
Firewall Two(Smoothie):
External: 98.214.xxx.xx2
Internal: 10.1.1.1 / 16  Forward to: 10.1.1.2(80) / 16
------------------------
Ubuntu 9.10:
Eth0: 10.1.0.3 / 16 
Eth1: 10.1.1.2 / 16 (apache2)
     VM1: 10.x.x.x / 16
     VM2: 10.x.x.x / 16
     VM3: 10.x.x.x / 16

---

