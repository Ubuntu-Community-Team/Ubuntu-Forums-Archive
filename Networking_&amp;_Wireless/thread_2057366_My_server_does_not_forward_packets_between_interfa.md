---
title: "My server does not forward packets between interfaces. What am I missing?"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by nhorst on 2012-09-13
I'd like to get my Ubuntu 11.04 server to route packet between its two network interfaces.

The two ethernet interfaces (eth0, eth1) work apparently well as such. 
Both have static IP addresses (192.168.2.15 & 192.168.3.15) and both are reachable from their respective network.
All IP services as well as the Samba server are reachable from both sides.

sysctl -p returns "net.ipv4.ip_forward=1" and I can even ping the interface "on the other side" from both networks.
In other words: I can ping 192.168.2.15 from all PCs on the 192.168.3.0 network and 192.168.3.15 from all systems 

on the 192.168.2.0 net. 
But I cannot reach any other address on the respective "other side"

I've already read numerous "how to" articles and Forum threads on this very topic of setting up Ubuntu as a router, 

but I just don't find the final solution to my problem.

Here are also some further information on the setup. 


Kernel IP routing table shows:
```
Destination	Gateway		Genmask		Flags	Metric	Ref	Use	Iface
default		192.168.3.1	0.0.0.0		UG	100	0	0	eth0
192.168.2.0	*		255.255.255.0	U	0	0	0	eth1
192.168.3.0	*		255.255.255.0	U	0	0	0	eth0

```
interfaces shows:
```

iface eth0 inet static
	address 192.168.3.15
	netmask 255.255.255.0
	broadcast 192.168.3.255
	network 192.168.3.0
        gateway 192.168.3.1


iface eth1 inet static
	address 192.168.2.15
	netmask 255.255.255.0
	broadcast 192.168.2.255
	network 192.168.2.0

```
I do not need any NAT or DHCP. There is no firewall running (no ufw, no iptables settings).
Both networks have their own firewall protected internet connection and the connected devices get their IP 

addresses from the respective internet routers. I just want to be able to reach for example printers on one network 

from clients on the other.

What am I missing? Does anyone have any idea?

Many thanks in advance!

---

### Post by mevun on 2012-09-13
Have you tried using traceroute on any of the other PCs?  That might help you figure out if your Ubuntu router is at fault or not.  I haven't dealt with networking in a while, so I don't actually remember what the output would look like, but there should be tutorials and such on the web.

---

### Post by nhorst on 2012-09-13
Yes, I did try tracert but since there is really only one hop to reach the target host it does not show much. 
In fact it did show the first hop to the respective network interface (192.168.x.15) but then timed out.

Thanks anyway for the hint!

---

### Post by OrangeMadness on 2012-09-17
I have been struggling with the same problem for the whole day. I am trying to setup an ubuntu server box to work as a router/firewall.

Decided I am going to go with iptables after all.   

Printed this tutorial for tomorrow:
[U][COLOR=Red][http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html](http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html)[/COLOR]
[/U] 
Also set up webmin (needed for shorewall)
[COLOR=Red][COLOR=Black]_[http://www.webmin.com/](http://www.webmin.com/)_[/COLOR]
[/COLOR] 
Shorewall is a firewall which is basically a front-end to iptables. 
_[COLOR=Red][http://www.shorewall.net/](http://www.shorewall.net/)[/COLOR]_
This really seems capable of doing the job.

Hope this helps you out. If you come across a better solution I am all ears.

---

### Post by OrangeMadness on 2012-09-19
Okay, IP forwarding is up and running. Should have kept detailed notes about this but I was under pressure to make it work within the day so I kept my hands on the keyboard.

On a fresh Ubuntu Server 12.04 installation:

1. Installed apache (apt-get install apache2)
2. Installed webmin - Downloaded .deb package from their site run dpkg -i webmin.deb showed some dependencies were not met
3. Used aptitude to install the 4 missing packages and run dpkg -i webmin.deb again

At this point webmin was available on [https://localhost:10000](https://localhost:10000)

4. Downloaded the shorewall module and installed on webmin through the web interface 
5. Did a trivial setup of the firewall, basically permitting everything and masqueraded eth2 (internal ethernet adapter) with eth0 (external ethernet adapter) 
6. Enabled IP_FORWARDING in shorewall.conf

-> Works like a charm

There must be easier ways, but my box is destined to be a firewall, hence I chose this way to get around this task. Now that forwarding is working I can start writing my rules without interrupting the network and internet access.

---

### Post by nhorst on 2012-09-19
Thanks, OrangeMadness!

I got it working finally when I added a masquerading rule in Shorewall.

Kind of strange that only after installing/enabling the firewall and masquerading one of the interfaces the system forwards packets from one side to the other... 

As you said:"There must be easier ways..." 
But anyway... Since it is running now I won't complain. :-)

Thanks again!

---

