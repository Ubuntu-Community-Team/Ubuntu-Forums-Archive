---
title: "troubleshooting hardwired home network"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by opfeld on 2012-07-20
I have three computers all hooked up by ethernet cables to the same router, desktop-ubuntu 12, laptop mint 12, and htpc ubuntu 12.  I have set some folders on the desktop to be shared across the network.  The laptop see them perfectly, however the htpc has trouble finding anything on the network.  When I try to browse the network on the htpc I just get an error saying saying the server never replied but when I do the same on the laptop it see the desktop and can open its folders fine.  This same thing was a problem when the htpc was using linux mint 11, I thought switching it to ubuntu would fix it but no.  Any suggestions on how to fix this?

---

### Post by papibe on 2012-07-20
Hi opfeld.

I would first compare the basic network setting on all machines:
```
ifconfig
```
To see they get a valid IP inside the LAN.
```
route -n
```
To see if they have a gateway to internet, and
```
nslookup ubuntu.com

dig ubuntu.com
```
To check if their DNS is well configured.

Let us know if you find a something unique on the htpc machine (or if not).
Regards.

---

### Post by opfeld on 2012-07-21
Well I have set up static ip's on all the computers, to make it easier to find them.  So they all have their own unique ip's, and I used namebench to get 3 dns servers for each computer, and then they all have the same netmask and gateway, is that correct?

---

### Post by opfeld on 2012-07-21
Also I can ping from the htpc to desktop and vice versa no problems

---

### Post by papibe on 2012-07-21
> **opfeld said:**
> Well I have set up static ip's on all the computers, to make it easier to find them.  So they all have their own unique ip's, and I used namebench to get 3 dns servers for each computer, and then they all have the same netmask and gateway, is that correct?

One of advantages of using namebench is that you'll have a faster Internet access. However, since you DNS is not in your LAN, the machines won't know each other by name, just by LAN IP address.

One solution could be to install avahi-daemon in all machines, so they can use broadcast to discover each other. That way you could access another machine using a .local domain. For instance:
```
htpc.local
```

Another simple solution could be to add all the machines and its LAN IPs, to all /etc/hosts that way they could access each other by short name.

I hope that points you in the right direction.

Let us know how it goes.
Regards.

---

### Post by opfeld on 2012-07-22
Well I found this 
[https://help.ubuntu.com/10.04/internet/C/networking-shares.html](https://help.ubuntu.com/10.04/internet/C/networking-shares.html)

and using the shares-admin cmd line I was able to get the network up and running fairly well, a little problem with ownership of the transferred files but I am working on that.  Thanks for all the help

---

### Post by opfeld on 2012-07-22
Well i can still see all the computer connected to the network so thats a step in the right direction, but now I keep getting the error unable to mount, from what I'm finding this seems to be a common problem, any sure fire solutions?

---

### Post by papibe on 2012-07-23
Could you post the command your are using to mount, and the errors you are getting? 

Regards.

---

