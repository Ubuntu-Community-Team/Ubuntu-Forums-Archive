---
title: "System ignoring /etc/networking/interfaces"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by deadtom on 2012-03-13
I have an ubuntu box handling DHCP and DNS on my network.

I have eth0 set to static for my internal network and eth1 set to DHCP  and connected to my cable modem. I manage these through  /etc/network/interfaces:

```

auto lo eth0 eth1
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet static
        address 192.168.58.1
        netmask 255.255.255.0
        broadcast 192.168.58.255
        network 192.168.58.0

iface eth1 inet dhcp
dns-nameservers 192.168.58.1
pre-up iptables-restore < /etc/iptables.rules

```But now it seems that the system no longer pays  attention to the interfaces file. As of last Thursday, every time I reboot, eth0 grabs an IP of 192.168.58.32, which happens to be the last IP in the pool that the system gives out via DHCP. 

I'm assuming that one of the updates I downloaded last week changed the way that ubuntu manages interfaces and /etc/network/interfaces is no longer the method for that.

So how do I now tell the system that I want eth0 to be static?

---

### Post by deadtom on 2012-03-15
OK, I figured out what's doing it, I just don't understand why or how to get it to stop.

Every day at 6pm, avahi-autoipd kicks on, ignores my static IP setting and issues eth0 the .32 address. I also noticed in my logs that eth0 is making DHCP requests all day long, about every 5 seconds. I don't understand this either as again, I have /etc/network/interfaces set up to give eth0 a static IP.

There are no cron jobs set up to do anything at 6pm. So I don't know where this is coming from.

Still no resolution.

---

### Post by deadtom on 2012-03-15
I have no idea what avahi does but I can't have my network going down every day.

*sudo apt-get remove avahi-daemon*

Problem solved.

---

