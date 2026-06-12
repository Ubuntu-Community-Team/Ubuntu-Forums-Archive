---
title: "IP address issues"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by tobyrose115 on 2010-08-12
Am attempting to set a static IP address on a server (to be used with Mythtv) and is running mythbuntu 10.04 (apologies if this is the wrong place to post this).

I can set a static IP address that is in the range of 192.168.1.x on other machines on the network but when I try with the server it is not able to connect to the network.  When using the DHCP rather than manually assigning the address it is assigned an address with the 10.0.0.x range. Why is it doing this I have never have this problem on other ubuntu boxes (and this one prior to a format of the OS).

The router/gateway is 192.168.1.1

I did have a DHCP server on the mythbox before formatting it and I was able to assign a static 192.168 address and retain internet connectivity. But I have re-enabled the DHCP server on my router since formatting the box. 

Regards

Toby

---

### Post by Kerubu on 2010-08-12
> **tobyrose115 said:**
> Am attempting to set a static IP address on a server (to be used with Mythtv) and is running mythbuntu 10.04 (apologies if this is the wrong place to post this).

I can set a static IP address that is in the range of 192.168.1.x on other machines on the network but when I try with the server it is not able to connect to the network.  When using the DHCP rather than manually assigning the address it is assigned an address with the 10.0.0.x range. Why is it doing this I have never have this problem on other ubuntu boxes (and this one prior to a format of the OS).

The router/gateway is 192.168.1.1

I did have a DHCP server on the mythbox before formatting it and I was able to assign a static 192.168 address and retain internet connectivity. But I have re-enabled the DHCP server on my router since formatting the box. 

Regards

Toby

I assume your wireless base is acting as your DHCP server. It might be possible that on your Ubuntu server is also running a DHCP server and assigning an address to itself (hence the address of 10.0.0.x).

to see if you have a DHCP server installed you can try using aptitude to see if the package has been installed :

aptitude search dhcp3

post the results here.

---

