---
title: "Strange network connection."
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by skaramanger on 2010-03-26
Greetings,

Recently I was checking out Hardinfo 0.5c and noticed that there were some ip connections listed as ESTABLISHED when I had no browser or other internet software active afaik.

I decided that since I knew not how to flush those connections to bring down eth0, my wired connection and only connection for this box.  So I did:

```
sudo ifdown eth0
```
then
```
sudo ifup eth0
```

My connection is static setup in /etc/network/interfaces. The interface took a short while to return to the prompt.  I do an:

```
ifconfig eth0
```

shows the system is up. However, when I ping  my router, I get a 100% loss.  I tried:

```
sudo /etc/init.d/networking restart/force-reload/stop/start
```

all the available of above to try and reset the connection and bring up the network. No go.

I then tried:
```
arp
```

It returned my routers ip address and I noticed something funny no mac address. So I just rebooted the machine and normal operation returned. I ran arp again and this is what was returned:


```
[myuser@mydesktop ~]$arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   00:18:01:6c:03:5f   C                     eth0
[myuser@mydesktop ~]$
```


This looks more like it.  After all this my question is: What could I have done to flush a cache or reset the network to allow a simple reconnection w/o incident?  I'm running Ubuntu 9.10, I removed network manager. 


[myusertmydesktop ~]$ uname -a
Linux mydesktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux
[myuser@mydesktop ~]$ 

[myuser@myudesktop ~]$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
	address 192.168.1.120
	broadcast 192.168.1.255
	network 192.168.1.0
	netmask 255.255.255.0
	gateway 192.168.1.1
	mtu 1492
[myuser@mydesktop ~]$ 



Thanks,
Skaramanger

---

### Post by doas777 on 2010-03-26
lots of apps use local only network ports to allow processes to communicate with eachother. what ports are these connections to, and if you run netstat, what apps are they connected to?

theoretically an arp flood could do weird things to your arp table, but somone would have to be able to get onto your local network to initiate one.

---

### Post by skaramanger on 2010-03-26
doas777 thanks for your reply,

> **doas777 said:**
> lots of apps use local only network ports to allow processes to communicate with eachother. what ports are these connections to, and if you run netstat, what apps are they connected to?

Ooops, I failed to make clear that that theses connections were to my local ip from an outside source.  They were definitely not from local host to itself. I did use zenmap to check a couple of those ips, but I didn't save them and rebooting did clear up the problem.


theoretically an arp flood could do weird things to your arp table, but somone would have to be able to get onto your local network to initiate one.

Yeah, is there a way to clear the arp cache?  I have 2 firewalls running one on my router and shorewall on my box.  My router's wireless is security is set to use wpa.

Thanks again

---

