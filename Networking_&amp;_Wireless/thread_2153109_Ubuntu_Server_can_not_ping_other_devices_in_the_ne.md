---
title: "Ubuntu Server can not ping other devices in the network"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by LarsEbert on 2013-06-10
Hello everyone!

I seem to have a very strange problem with my network setup. My Ubuntu-Server can not ping or reach other devices in the network (except the gateway) but the other way around it is possible.

Let me describe the general setup:

I have a router with the IP 192.168.2.1 which acts as a DHCP-Server and hands out addresses in the range 192.168.2.10 - 192.168.2.100.
The Ubuntu-Server is configured with the static IP 192.168.2.2 so its IP does not change and it can be accessed.
There are some other devices in the network getting IPs from the router, for example my windows machine currently has the IP 192.168.2.11.
From my windows machine, it is possible to ping all the devices in the network, including the server. But on the server, I only am able to ping 192.168.2.1 - all other connections are timing out.
The internet connection seems to work fine on all devices, only the communication from my server to other devices does not work.

Here are the configurations of the devices involved:

Windows machine:
DHCP: Yes
IP: 192.168.2.11
Subnetmask: 255.255.255.0
Gateway: 192.168.2.1
(These all are assigned by the DHCP-Server)

Ubuntu-Server:
eth0
IP: 192.168.2.2
Bcast: 192.168.2.255
Mask: 255.255.255.0

/etc/network/interface
auto eth0
iface eth0 inet static
address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1

Does anyone have a clue why pinging the other devices from my server is not working? I am very confused, as it works the other way around.

I am glad for any help! Thank you all!

---

### Post by The Cog on 2013-06-10
My first reaction is to wonder if there is another 192.168.2.2 anywhere on the network. Are the other machines still able to ping 192.168.2.2 when the ubuntu server is disconnected?

My second reaction is to wonder if you have configured some firewall rules that prevent pings working properly. Please post the output of this command which prints all of the firewall rules and their hit counts. If  it doesn't print anything, that's OK, just say so.
```
sudo iptables-save -c
```

Also, while trying to ping something from ubuntu in one window, please run these two commands in another window and post the results, it prints the ip addresses and arp tables:
```
ip a
ip n

```

---

### Post by LarsEbert on 2013-06-10
Hey! Thank you for your answer.

I just ruled out the possibility of a second device using 192.168.2.2, after disconnecting the server, 192.168.2.2 does not reply to pings.

I do not use any firewall on my windows devices and I do not think that I use a firewall on the ubuntu server. At least I did not install one. Is there one installed by default with ubuntu server 12.04?

Running sudo iptables-save -c did not output anything. Is that good or bad?

While pinging 192.168.2.11 from the server, ip a echoes this:

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
        valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 150 qdisc pfifo_fast state UP qlen 1000
    link/ether 08:06:6e:e6:23:57 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.2/24 brd 192.168.2.255 scope global eth0
    inet6 fe80:e60:6eff:fee6:2357/64 scope link
        valid_lft forever preferred_lft forever
```

ip n echoes:

```
192.168.2.11 dev eth0 lladdr 6c:f0:49:98:e8:a5 REACHABLE
```

What now?

Edit: I also noticed that [http://192.168.2.2](http://192.168.2.2) is not working, the server does not respond although an apache is up and running.

Edit 2: It seems the problem has nothing to do with DHCP. I just activated DHCP for the Server and the problem still ocurrs. The problem seems not to end with pings or http-requests: connecting to the server via SSH also is impossible, the connection just times out. How do I find any firewalls set up by ubuntu? I am not aware of any firewall running but maybe I missed something?

---

### Post by The Cog on 2013-06-10
> I do not use any firewall on my windows devices and I do not think that I use a firewall on the ubuntu server. At least I did not install one. Is there one installed by default with ubuntu server 12.04?
I don't normally use a firewall. Ubuntu doesn't accept incoming connections unless you start a server process anyway, and if you start a server process you probably want people to be able to connect to it. So installing a firewall is a bit like building a wall just so you can knock a gateway into it. iptables is the inbuilt firewall command set, but by default it allows everything in and out. As iptables can be complicated to configure there are firewall programs (ufw is recommended)  that configure iptables for you. 
> Running sudo iptables-save -c did not output anything. Is that good or bad?
That's OK. It just means that iptables has no rules configured - as I say, its default is to allow everything. No harm because the OS will just send connection refused if there's no server listening for connections anyway.

Your "ip a" shows the address/mask is as we expected. Just double-checking.
Your "ip n" shows that neighbour 192.168.2.11 is reachable. It is answering ARP requests. At this point, I wonder if 192.168.2.11 has a firewall configuration that prevents it answering pings.
The only thing you can do further is to use 
```
sudo tcpdump -np -i eth0
```
to watch packets going in and out. I expect to see ping requests but no reply.

> Edit: I also noticed that [http://192.168.2.2](http://192.168.2.2) is not working, the server does not respond although an apache is up and running.
A default apache install only listens on loopback 127.0.0.1. the configuration for this is in either /etc/default/apache2 or /etc/apache2/httpd.conf. I think they're the right filenames, but I forget which you need to edit - try default first. Then restart apache.

---

### Post by LarsEbert on 2013-06-10
Crap, I just had the Idea to try and ping another Windows machine in the network. It worked. Accessing the Webserver also works. It seems there is a problem with my windows machine, the server works just fine.

I am sorry for this confusion. Tomorrow I shall debug my windows machine, but for today, I say g'night!

Edit: Sorry again for bothering you all. It turns out that simply rebooting the windows machine fixed everything. :(

---

### Post by The Cog on 2013-06-11
That's OK. It's always nice to get a proper conclusion to an issue, even if it's an unexpected twist. And it all helps anyone else having similar problems.

---

