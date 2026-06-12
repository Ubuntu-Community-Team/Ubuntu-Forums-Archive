---
title: "Dual Homed How-To request"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by gregster on 2006-06-02
I have an nForce4 machine with dual onboard gigabit NICs (CK804). As long as I stick to using a single NIC for everything I'm fine, but the ideal setup would look like this:
* eth0 connects to one network and operates as my default NIC (all regular traffic goes through it) 
* eth1 is connected to a totally different physical network (different subnet/gateway, the works) and is used exclusively by virtual machines in VMWare (eth1 will be bridged to the vmnet virtual adapters)

I suspect that I'm looking for an iptables solution that will dualhome my machine, but I don't like experimenting with this without some advice first. If anyone can offer me a pointer or at least some search terms that I can use to get started I'd really appreciate it.

For what it's worth, I have no hardware problems at all. Both NICs work on either network, just not both simultaneously on different networks.

Thanks.

---

### Post by jvl on 2006-06-21
What does exactly mean "both nic don't work simultaneously on different networks"? Does that mean it's not routing? Can you ping another machines on the same networks? What is your default route? Please specify.

---

### Post by gregster on 2006-06-26
My goal was to have my nics operating simultaneously on separate networks. eth0 was to be my main nic connecting via a gigabit switch, while eth1 was to be connected to a 100baseT switch and only handle traffic from VMWare machines.

As I said, absolutely no problems getting either nic working, just not the way I describe above. When I set up the second nic through the GUI interface eth1 became the only nic that would make a connection (although eth0 was still activated and I would get the small "keep-alive" packets going out). I could change things to eth0 and it would work, but then all traffic went through eth0. Basically, I could either get traffic going through one or the other but not both simultaneously.

But I *think* I've resolved the problem on my own. As I said above, when I activated my second nic it appears as though it took over default duties. I changed my /etc/network/interfaces file to look like this:

auto lo
iface lo inet loopback

auto eth0 eth1
iface eth0 inet static
	address xxx.xxx.xxx.xxx
	netmask xxx.xxx.xxx.xxx
	network xxx.xxx.xxx.xxx
	broadcast xxx.xxx.xxx.xxx
	gateway xxx.xxx.xxx.xxx

	dns-nameservers xxx.xxx.xxx.xxx xxx.xxx.xxx.xxx
	dns-search mydomain.ca

iface eth1 inet static
	address yyy.yyy.yyy.yyy
	netmask yyy.yyy.yyy.yyy
	gateway yyy.yyy.yyy.yyy

And now it looks like I'm getting the behaviour I wanted.

---

### Post by jvl on 2006-06-27
why do you have gateway (i.e. default route) set on both NICs? Default route should be set only on the NIC connecting you to the internet.

---

### Post by gregster on 2006-06-27
The networks I'm connecting to have different gateways. Is it possible for a nic to use a gateway from a completely separate network?

---

### Post by mips on 2006-06-27
Yes it's possible but it is not the way you should do it. The one nic should point to the other one as a gateway but that is ONLY if you want all traffic to use the same gateway.

You need to disable routing between the two nics if you don't want the traffic to be forwarded.

---

### Post by gregster on 2006-12-04
Right, I think I finally understand!
I did this:
$ route
and got this back:
123.456.999.xxx   *       255.255.255.xyz U     0      0        0 eth1
172.36.1.0        *       255.255.255.0   U     0      0        0 vmnet8
192.168.1.0       *       255.255.255.0   U     0      0        0 vmnet1
123.456.777.xxx   *       255.255.255.0   U     0      0        0 eth0
default     123.456.999.xxx 0.0.0.0         UG    0      0        0 eth1
default     123.456.777.xxx 0.0.0.0         UG    0      0        0 eth0

My understanding is that this says that there are two default gateways (of course). I ran this:
sudo route del -net default eth0
which removed the "slow" network as a default.

I haven't tried rebooting yet, but I'm guessing that this won't stick through a reboot, so the next step is to somehow include this in an init script. Any thoughts on best practice?

---

### Post by mips on 2006-12-05
you could add it to you /etc/network/interfaces file under the specific interface.

Something to the effect of "up route del ...."

Not really related to your question but a nice article, [http://www.debian-administration.org/articles/377](http://www.debian-administration.org/articles/377)

---

