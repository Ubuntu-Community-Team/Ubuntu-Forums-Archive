---
title: "NetworkManager and dnsmasq-base dns issue"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by werzy33 on 2009-11-06
On an Ubuntu 9.10 desktop I have 2 interfaces: wlan0 and eth0.
wlan0 has a working connection to the internet
eth0 is connected to a router 

I have an Ubuntu 9.04 desktop that I am testing the interet sharing to the previously mentioned desktop; it has only 1 interface eth0.

NetworkManager is used to manage the networking, and eth0 has been configured via NetworkManager to "share to other computers".  

Everything works great IF I change the nameserver on the client that I wish to share the internet in its /etc/resolv.conf.  The nameserver that it gets is the Ubuntu desktop eth0 ip; it is changed to the nameserver of the ISP and all works as advertised.

Computer 1:
Ubuntu 9.10 Desktop
wlan0: connected to internet
eth0: ip = 10.42.43.1

Computer 2:
Ubuntu 9.04 Desktop
eth0: ip = 10.42.43.10
This is also managed by NetworkManager, to automatically setup via DHCP

Is the nameserver of computer 2 supposed to be 10.42.43.1?  If so, the dnsmasq-base/NetworkManager on computer 1 is not providing proper dns resolution, I would like to fix this.  Once again, my workaround is to change the nameserver to the one that is actually used by computer 1.

---

### Post by Iowan on 2009-11-06
What's in */etc/dnsmasq.conf*?

---

### Post by werzy33 on 2009-11-07
I did copy the example dnsmasq.conf file into /etc, it is all commented out, after trying a few things with it.  I don't think there was any /etc/dnsmasq.conf by default.  I had uncommented a few lines regarding "resolv.conf", but they are currently commented out.

---

### Post by Iowan on 2009-11-07
> **werzy33 said:**
>   If so, the dnsmasq-base/NetworkManager on computer 1 is not providing proper dns resolution, If there is no */etc/dnsmasq.conf*...
I'm using **dnsmaxq** for my local DHCP/DNS - it seems to work well for me...
Perhaps we could get a workable file built.

---

