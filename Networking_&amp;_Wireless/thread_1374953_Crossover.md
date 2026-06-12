---
title: "Crossover"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by warfacegod on 2010-01-07
I've periodically tried doing a direct connect between two computers for about 9 years with zero results. I cannot, for the life of me, understand why his is so difficult. Most of my attempts have been with Windows machines. My most recent attempt (today) has been with two Ubuntu 9.10 Linux machines. I have followed this thread.

[http://ubuntuforums.org/showthread.php?t=1350838]("http://ubuntuforums.org/showthread.php?t=1350838")

However, when I use ifconfig, it isn't showing the ip address under eth0.

Thanks in advance.

---

### Post by Iowan on 2010-01-07
The cable is a crossover(wire color sequence is different on each end)?

---

### Post by warfacegod on 2010-01-07
Yes. it even says Xover on it.

---

### Post by iponeverything on 2010-01-07
are you seeing link light?

What is the ip/netmask of the machine's on each side of the link?

---

### Post by iponeverything on 2010-01-07
Do it the easy way:

Machine 1:

open a terminal and run:

```
sudo nano /etc/network/interfaces

```
Add the following section:

```

iface eth0 inet static
  address 192.168.2.1
  netmask 255.255.255.0

auto eth0

```

Machine 2:

open a terminal and run:

```
sudo nano /etc/network/interfaces

```
Add the following section:

```

iface eth0 inet static
  address 192.168.2.2
  netmask 255.255.255.0

auto eth0

```

The two machines should now be able to ping each other.

now install openssh-server, and sshfs on both machines.

from the prompt of machine one:

```

mkdir machine2
sshfs yourusername@192.168.2.2:/home/ machine2

```

You should now see a folder with other machine show up on your desktop..

---

### Post by warfacegod on 2010-01-07
On only one but on my laptop, I don't think it will light up unless the connection is actually doing something.

ifconfig dooesn't show netmask under eth0

It's 255.255.255.0 under wlan0 on both in case that helps.

---

### Post by warfacegod on 2010-01-07
Okay, I can see why your above post should work so it makes no sense to me as to why it didn't. Your help, by the way, is greatly appreciated.

No folder is on the desktop but I can go to the folder in /Home and there is nothing in it. The machines are not getting replies when I ping.

---

### Post by iponeverything on 2010-01-07
while the cable is plugged in to both boxes, run:

```
sudo ethtool eth0
```

also make sure that the two machines don't have firewall rules that are preventing them from talking..

```

sudo iptables -L -n

```

---

### Post by warfacegod on 2010-01-07
```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: no
```

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by iponeverything on 2010-01-07
> **warfacegod said:**
> ```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	**[COLOR="Red"]Link detected: no[/COLOR]**
```

You might have a bad cable..

---

### Post by warfacegod on 2010-01-07
...And me with no way to find out. My internet access is wireless exclusively so I can't plug in the cat.5 to a router and see if I can connect to the net. Doing that would, of course, eliminate eth0 being broken. It will be several days before I can try that or I'll just go buy another crossover cable. I'll post back with the results as soon as I can. Thanks for all of your help!

---

### Post by warfacegod on 2010-01-12
Yup, the crossover cable was bad. Everything works now, thanks!

---

