---
title: "Ad-hoc with iphone tethering"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by pssturges on 2010-09-18
Hi,

I am trying to create a wifi network based around my ubuntu laptop with my iphone 3g tethered to it by usb cable for an internet connection. I would like to be able to share this internet connection with other devices that connect to this network and and perform various other network functions between devices on this network such as smb file sharing and ssh. Primarily I am testing this with my ipad, but would like to add other devices as needed.

So far I can successfully tether my iphone to my laptop and browse internet on my laptop. Connection information in the network manager shows:

eth2
ip address:172.10.20.3
broadcast address: 172.10.20.15
sunet mask:255.255.255.240
default route: 172.10.20.1
primary dns: 202.81.67.132
secondary dns: 202.124.65.18

Now I create my ad hoc network via network manager using default settings and connect my ipad. This process appears to work. I have the wifi connection icon on the top left hand corner of the ipad but I have no internet connectivity on the ipad. Connection information in network manager for my wifi connection shows:

ip address:10.42.43.1
broadcast address: 10.42.43.1
sunet mask:255.255.255.0

The connection info on my ipad shows:
ip address:169.254.196.133
sunet mask:255.255.0.0
Router: empty
DNS: empty
Search Domains: empty
Client ID: empty

Am I going to need to install and configure a dhcp server? Is there some other way of doing this?

Thanks for any help,
Phil

---

