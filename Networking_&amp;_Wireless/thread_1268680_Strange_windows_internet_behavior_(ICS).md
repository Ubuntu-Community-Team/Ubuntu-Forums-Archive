---
title: "Strange windows internet behavior (ICS)"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by lvlint67 on 2009-09-17
So here on campus we are not allowed to run routers and they only give us one Ethernet port. Several students and myself have had success in the past using ubuntu based servers to act as a gateway to allow multiple computers in the room to access the network.

Before I installed XUbuntu and used firestarter and a series of prayers to get it to work.
This year, so far, I have been using my windows server 2k8 computer (main pc) as the ics supplier... I'm ready to switch that again as I'm going to format this computer (winserv) and dual boot serv2k8 and linux mint.

--------------
I installed ubuntu-server (latest)
and used these commands as per an online tutorial:
```

ifconfig eth1 192.168.0.3
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward (I actually used nano here)
sudo apt-get install dnsmasq ipmasq
/etc/init.d/dnsmasq restart
dpkg-reconfigure ipmasq
--(I went through and pretty much accepted the defaults)---
ifconfig eth1 192.168.0.3
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```Add the line "net.ipv4.ip_forward = 1" to /etc/sysctl.conf
gedit /etc/sysctl.conf
--------------------------------------
eth0 is set to dhcp and connects to the wall (campus network)
eth1 connects to a switch which is then connected to my windows computer
-------------------------------------

To log into the network like this I use virtualBox to run linuxMint with the network cards bridged.

both windows and linux mint (in virtualbox) can ping google.com, eachother, and the gateway ip
(when i say ping i mean windows resolves the name, the campus blocks incoming pings so nothing actually gets a response outside of the campus network)

the linux vm and the ubuntu gateway can ping campus ips
windows apparently is not as social in that reguard

the linux vm can browse the internet freely with firefox.
The windows machine with firefox wont connect to the server
>telnet google.com 80
fails to connect but it can still resolve names.

I installed openssh-server on the linux vm and using putty i can ssh in and use a proxy...

setting everything up and having firefox in windows use localhost:5252 (my chosen settings) as the socks4 proxy host i can freely browse the internet with windows.

^^That is ridiculous since the linux vm connection is coming through the same nic as the windows connection... :(

**Anyone have ideas to fix this craziness?**

--------============-----------========
settings:
server->Ubuntu Server
--eth0
-----address dhcp (from campus
--eth1 static
----address 192.168.0.3
----network 192.168.0.0
----subnet 255.255.255.0
----gateway 192.168.0.3

Windows server
--eth0 static
----address 192.168.0.60
----subnet 255.255.255.0
----gateway 192.168.0.3
----dns 192.168.0.3

Linux server (bridged with windows eth0)
--eth0 static
----address 192.168.0.69
----network 192.168.0.0
----subnet 255.255.255.0
----gateway 192.168.0.3

---

### Post by Iowan on 2009-09-17
I presume a common switch/hub doesn't work to expand the port?

---

### Post by lvlint67 on 2009-09-18
> **Iowan said:**
> I presume a common switch/hub doesn't work to expand the port?

No. The campus switches are anal about how many computers can be attached to one port.

---

