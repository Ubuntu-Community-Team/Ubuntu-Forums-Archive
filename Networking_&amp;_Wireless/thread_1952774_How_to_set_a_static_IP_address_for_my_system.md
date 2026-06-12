---
title: "How to set a static IP address for my system"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by unckybob on 2012-04-04
If it seems like I don't know what I am doing, it is because I don't.

I am not lazy or stupid though. I am reading Scott Mueller's "Upgrading and Repairing PCs" series. I haven't made it through "Upgrading and Repairing Networks" yet. 

Right now I am trying to install a type of firmware to a router that will make it into a repeater. If I can make it work, I can mount it on my van to get wifi hotspots. I'm kind of living out of it right now.

I can also use a USB powered wifi device mounted to an antenna, but then I will have to wire 20 gauge USB wire all over my van. As well as USB hubs to boost the signal. You can use 20 gauge USB cables for up to 5 meters. After that you can use a powered USB hub to get another 5 meters. (I told you I wasn't stupid or lazy). That will be a real mess.

So if you would help me with a few noob questions, it will be a real help.

Can someone please tell me how to set a static IP address on my system?

---

### Post by mikewhatever on 2012-04-04
Check out the link: [http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-assign-static-ip-address-in-ubuntu-linux/)

---

### Post by unckybob on 2012-04-04
Thank you so much for a quick reply.

I guess I need more information:

Static IP address
Netmask
Gateway
DNS Server
Search Domains

Another post suggested I could find these using the command "route -n". I ran the command and here's what I got:

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
#

Is the information there?

---

### Post by bab1 on 2012-04-05
> **unckybob said:**
> Thank you so much for a quick reply.

I guess I need more information:

Static IP address
Netmask
Gateway
DNS Server
Search Domains

Another post suggested I could find these using the command "route -n". I ran the command and here's what I got:

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
#

Is the information there?
Some of it is.  It appears that the network card is configured with the label **eth0**. The route command shows the netmask as ```
192.168.1.0     0.0.0.0         [COLOR="Red"]255.255.255.0[/COLOR]   U     1      0        0 [COLOR="Red"]eth0[/COLOR]
```gateway as```
0.0.0.0         **[COLOR="Red"]192.168.1.1[/COLOR]**     0.0.0.0         [COLOR="Red"]UG[/COLOR]    0      0
``` The info not there can be found using the following commands:

IP address ```
ifconfig
``` 

DNS info ```
cat /etc/resolv.conf
```

The man pages will explain it all, see ```
man ifconfig
man interfaces
man resolv.conf
```

---

