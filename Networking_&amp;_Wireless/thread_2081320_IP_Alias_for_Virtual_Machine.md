---
title: "IP Alias for Virtual Machine"
date: 2012-11-06
forum: Networking &amp; Wireless
---

### Post by gregintexas on 2012-11-06
Hi Everybody;

Thank you in advance for any help you can give. I have searched and searched and have not found an answer to my issue. I'm not sure if this should be in virtualisation or networking - since it's mostly a networking question, I'll ask here.

I have a rent-a-server with one NIC and two real-world IP addresses. The first IP, 69.xxx.xxx.xxx, is the actual IP address of the server. The second IP, 209.xxx.xxx.xxx, is an IP alias. The interface is defined as follows:

```
  # loopback interface

  auto lo
  iface lo inet loopback

  # ethernet interface

  auto eth0
  iface eth0 inet static
    address 69.xxx.xxx.xxx
    network 69.xxx.xxx.0
    netmask 255.255.255.0
    broadcast 69.xxx.xxx.255
    gateway 69.xxx.xxx.1

  # virtual interfaces

  auto eth0:0
  iface eth0:0 inet static
  name Ethernet alias LAN card
  address 209.xxx.xxx.xxx
  netmask 255.255.255.255
```
The 69.xxx.xxx.xxx address has a web server and a number of functioning services on it. The 209.xxx.xxx.xxx address is a recently purchased address. It "pings" as defined above. I've no previous experience with IP aliases, but as I understand it, the address is NOT associated with a network at all. There is no broadcast or gateway associated with the address.

I am attempting to install a product that functions within a virtual machine hosted on the same server. I want the virtual machine to be addressed by the 209.xxx.xxx.xxx address. The pre-built VMWare based virtual machine obtains its IP through DHCP. Both the host and virtual machine are Ubuntu 10.04 server. I would prefer to change the VM to use the 209.xxx.xxx.xxx static IP, but have no idea how to set that up since there is no actual network/broadcast/gateway. When I attempt to set up the dhcp3-server on the host, it fails to start, issuing the error message: "No subnet declaration for eth0:0 (0.0.0.0). ** Ignoring requests on eth0:0." as if the eth0:0 interface is not up. The eth0:0 is, however, up.

Anyone know how to set the above scenerio up? Is it even possible with an IP alias?

Thanks,

gregintexas

---

### Post by gregintexas on 2012-11-06
I forgot to mention that Bridged networking is implemented on the virtual machine per the instructions of the product being installed. Thanks again!

---

### Post by gregintexas on 2012-11-06
Please! If anyone knows that the above is impossible, respond to this thread. I've spent hours and hours on this problem. If it is possible, how in the heck do you do it?

---

