---
title: "port forwarding woes to web server"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by iruff on 2009-12-16
Hi all... trying to convince our staff that Ubuntu Server is a better way to go than Windows Server, but I'm stuck getting this port forwarding working.

I have Tomcat installed (port 8080) on Ubuntu Server 9.04. UFW is disabled. I have a dual port nic, with one port connected to a router on our private local network, and a second port connected to a router on our public local network. Each router (both are Linksys WRT320N) is directly connected to our modem.

My /etc/network/interfaces

```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp 

## This is the network bridge declaration
auto br0 ## start on boot
iface br0 inet dhcp
  bridge_ports eth1

iface eth1 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down
```Both routers are configured to assign IP's based on MAC address. 

eth1 is bridged for some OpenVPN goodness, and it is the port connected to my local private network, leaving eth0 connected to our public network.

Steps I've Taken:
1) Set up port forwarding from modem to router
     -- Port 80 inbound forwarded to port 80 on public local router
2) Set up port forwarding from router to server
     -- Port 80 inbound forwarded to port 8080 on Ubuntu server
3) Confirmed UFW is inactive
4) Confirmed that I can hit web server from local network from a web browser

I would expect then to be able to then also hit my web server from a browser coming in from the world wide web.. but it just doesn't work. I can see log messages on the router where I've made the attempt from the web, but that's as far as it gets. What further complicates the matter is that I can take my laptop, with Ubuntu 9.10, a single network port, tomcat running on 8080, and it works from a browser over the web! What gives?

Please help!
Thanks
iruff

---

### Post by shairozan on 2009-12-16
Hey there, 

When you say

> What further complicates the matter is that I can take my laptop, with Ubuntu 9.10, a single network port, tomcat running on 8080, and it works from a browser over the web! 

What do you mean? Do you mean that you have tomcat installed on your private network, and you can browse to it from there? 

I think what you may be looking at is the NAT limitations imposed by your router. I had a similar issue recently trying to "get all I can out of a single IP address." All of my sites are hosted off of a single IP address, but I wanted to host multiple sites. Thus I just figured I would have a primary webserver (using port 80) and link to all of the others (using non standard ports such as 3000 and 5000)

I'm used to working with Cisco routers which allow you to do NAT overload, or take incoming packets to 1.2.3.4 on port 80 and send them to internal server 4.2.3.1 port 8080. Port forwarding is different, however, and literally just forwards your TCP queries to the internal server, but the port is not changing. You also cannot combine port forwarding on the router with another service. 

Here's a quick test. Take your public URL (whatever the public IP address of the server you're trying to access) and instead of just putting [www.mydomain.com](www.mydomain.com) enter [www.mydomain.com:8080](www.mydomain.com:8080) and see if that works. If that's the case, you're router is the primary limiting factor.

---

### Post by iruff on 2009-12-16
Thanks for the reply :)

When I say that it works on my laptop, what I'm saying is that I can use the same physical configuration (www -> modem -> router -> computer) and port forwarding rules, only substituting the local ip of my laptop instead of the local ip of my server, and I can successfully serve web content to the world. The difference from my perspective seems to be either a difference in (a) Ubuntu Server vs. Ubuntu Desktop, or (b) in how my router forwards traffic to my web server (2 network ports, each on different subnet, but 1 obviously the same as the router) vs to my laptop (1 network port)

I'm only trying to serve up one site. This has to be possible, right?

If I try mydomain.com, I can see in my router logs where an http request is made to my web server's ip, bearing in mind that my modem is configured to route traffic on port 80 to the router. If I try mydomain.com:8080, I don't get anything, which I don't think is unexpected because my modem is not configured to pass that traffic along, nor is the modem's web config interface accessible from 8080 (or the web for that matter).

So.... is there a difference in how Ubuntu Server and Desktop would handle a request made from an IP on a different subnet? Does firewall come into play here if UFW is inactive?

---

