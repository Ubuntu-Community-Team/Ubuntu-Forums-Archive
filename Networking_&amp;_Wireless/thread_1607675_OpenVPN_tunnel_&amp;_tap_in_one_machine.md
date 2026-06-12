---
title: "OpenVPN: tunnel &amp; tap in one machine"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by wowiesy on 2010-10-28
I have set up an OpenVPN via routing on an Ubuntu 9.04 machine in the office.  I use this VPN link when I am offsite and I need to connect to the office to get some data.  I do not have problems with this since I can manage on my own if there are issues.  However, I now need to also enable this VPN link to other users which are not as technically knowledgeable.  

I am now thinking of offering 2 services (routing and ethernet bridging) on the same VPN box. 

Can I do this on the exact same machine (no additional LAN card)? The links I've seen over the web on tutorials on how to setup OpenVPN Ethernet bridging mostly only only have bridging and no routing (tap only, tun not included)...  I somehow think I need to have to eth devices (eth0 for the actual LAN card which is used by OpenVPN tun device) and another, eth1 device to be bridged... how do I setup the scripts?

---

### Post by SeijiSensei on 2010-10-28
I generally avoid bridging and prefer routing instead.  What do you see these other users doing over these tunnels?  Why would they need bridging?

If you have a small set of users, you could just set up unique tunnels using different port addresses for each one.

If the idea is to allow the remote users to appear to the internal network as if they're on the VPN server, just use iptables to masquerade their traffic.  

```
iptables -t nat -A POSTROUTING -i tun0 -o eth0 -j MASQUERADE
```

makes all traffic arriving on tun0 for destinations outside the box itself to appear to be coming from the IP address on eth0.

You need to set 'net.ipv4.ip_forward' in /etc/sysctl.conf to 1 to enable routing; reboot to make it happen.

---

### Post by wowiesy on 2010-10-29
My idea is just so that the vpn user is able to browse the network neighborhood without having to know the ip address of each specific server he needs to get into, much like how it is setup in the LAN right now..  

Since I am now mostly using a Mac and just logging into the linux boxes through ssh, I could manage on my own, knowing all the ip addresses of the other servers.  

I could actually leave the setup as it is right now and just give them the list of ip addresses and hostnames to serve as their references. 

Another reason is curiousity: I've been using routing ever since I setup OpenVPN, I also want to see the difference with ethernet bridging so I can know for myself, although I am not sure since I'm mostly using a Mac, if I'd be able to appreciate the differences...

---

### Post by SeijiSensei on 2010-10-29
> **wowiesy said:**
> My idea is just so that the vpn user is able to browse the network neighborhood without having to know the ip address of each specific server he needs to get into, much like how it is setup in the LAN right now.

Do you have a WINS server or an internal DNS server?  You can use the OpenVPN "push" option to tell the client what internal servers to use for name resolution.  See [http://openvpn.net/index.php/open-source/documentation/howto.html#dhcp](http://openvpn.net/index.php/open-source/documentation/howto.html#dhcp) for details.

---

### Post by mikeygstl on 2011-12-20
> **SeijiSensei said:**
> Do you have a WINS server or an internal DNS server?  You can use the OpenVPN "push" option to tell the client what internal servers to use for name resolution.  See [http://openvpn.net/index.php/open-source/documentation/howto.html#dhcp](http://openvpn.net/index.php/open-source/documentation/howto.html#dhcp) for details.

Why the reluctance to utilize a bridge?  Seems a bridge, allowing the internal DHCP server to manage the VPN clients, would fit their needs perfectly.  The security aspect of manageing VPN client access to services seperately does not seem to be a concern.

I believe you will find all the pertinant information here:

[http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html](http://openvpn.net/index.php/open-source/documentation/miscellaneous/76-ethernet-bridging.html)

They key here is to set up your bridge without losing connectivity during the process.  I have done this a few times, and now have a dedicated nic for 'backup' access... ;)

---

