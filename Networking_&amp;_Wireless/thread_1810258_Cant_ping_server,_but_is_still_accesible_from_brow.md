---
title: "Cant ping server, but is still accesible from browser?"
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by tottenham12712 on 2011-07-22
Hey guys so I have a very strange issue with my webserver. It resides at 65.211.112.135 There are numerous domain names on this ip [www.barrierfree.us](www.barrierfree.us), [www.barriercom.net](www.barriercom.net), [www.eventsfx.com](www.eventsfx.com), [www.fireislandnews.info](www.fireislandnews.info) Those are a few of them. Now if you try to ping 65.211.112.135 it does not respond, if you ping "www.barrierfree.us" it says pinging 65.211.112.135 but it also does not respond. BUT if you point your browser to one of the above domain names it will work, but it is quite slow. I am confused as to how this could happen. Any ideas would be of use.

---

### Post by e79 on 2011-07-22
1. You should not give real network/domain names info like that on any forums, unless you wants trouble with people trying to hack your servers (please mods, erase/replace the OP external IP/domains info with cherry pies :D).

2. ICMP (ping request as example) and Web/http (port tcp 80) are 2 totally different things. 

3. What I see here is simply a firewall doing its job, blocking ICMP requests while allowing web requests to get to your servers.

---

### Post by tottenham12712 on 2011-07-22
> **e79 said:**
> 1. You should not give real network/domain names info like that on any forums, unless you wants trouble with people trying to hack your servers (please mods, erase/replace the OP external IP/domains info with cherry pies :D).

2. ICMP (ping request as example) and Web/http (port tcp 80) are 2 totally different things. 

3. What I see here is simply a firewall doing its job, blocking ICMP requests while allowing web requests to get to your servers.

Its a webserver therefore you just ping the domain name and you get the IP address. The firewall is not doing its job because currently it is set to allow pings

---

### Post by e79 on 2011-07-22
> **tottenham12712 said:**
> Its a webserver therefore you just ping the domain name and you get the IP address.

I was simply trying to avoid you some troubles. people usually do not give their real external IP addresses or domain name.

> **tottenham12712 said:**
>  The firewall is not doing its job because currently it is set to allow pings 
If the firewall is set to allow Ping requests, is it possible there is a firewall on the server that blocks/drop it ?

---

### Post by tottenham12712 on 2011-07-22
> **e79 said:**
> I was simply trying to avoid you some troubles. people usually do not give their real external IP addresses or domain name.


If the firewall is set to allow Ping requests, is it possible there is a firewall on the server that blocks/drop it ?
 

Wasnt trying to be an a$$ but its a webserver so its already visible to the world. I would never reveal the IP to a critical network device.

There was a firewall and i set it to allow pings, now i completely uninstalled it and i still dont get a response. If i do a network reset it comes up with an error stating it can not bring up eth0. Could that be the issue? But if i issue ifconfig it says its up ok and if i use nslookup it works correctly and so does a ping to any website (all of which is executed via the server itself). Im stumped, I hate being stumped lol:confused:

---

### Post by e79 on 2011-07-22
> There was a firewall and i set it to allow pings, now i completely uninstalled it and i still dont get a response.

Does the server answers to ping locally (logged in from SSH per example, and pinging local host) ? or is it possible then that it is being blocked at the ISP level ?

> If i do a network reset it comes up with an error stating it can not bring up eth0. Could that be the issue?

Can we perhaps see you interfaces file ?

```
cat /etc/network/interfaces
```

---

### Post by tottenham12712 on 2011-07-22
> **e79 said:**
> Does the server answers to ping locally (logged in from SSH per example, and pinging local host) ? or is it possible then that it is being blocked at the ISP level ?



Can we perhaps see you interfaces file ?

```
cat /etc/network/interfaces
```

I can ping locally LAN. I cant ping on the WAN. We are the ISP for fire island (the company I work for) so our feed is a carrier grade fiber feed, everything is open. We do have a gateway in between the router and all network devices but the webserver is on a Pass through rule to allow all network traffic through.

This is why im so stumped 

Interfaces file: 
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
 # The loopback network interface
auto lo
iface lo inet loopback
 # The primary network interface
 
 auto eth0
iface eth0 inet static
address 65.211.112.135
gateway 65.211.112.129
netmask 255.255.255.128
broadcast 65.211.112.255

```

---

### Post by e79 on 2011-07-22
I am running out of ideas...

your interfaces file seems correct apart not having the network definition (which I believe should be 65.211.112.128)  and maybe a 'space' at the beginning (just before 'auto eth0') but I don't think its related to the problem at all...

I also thought about the config of '/proc/sys/net/ipv4/icmp_echo_ignore_all' (or something related) but it is irrelevant since the ping works on the LAN side....

I'll keep seeking and will come back if I find anything else

---

### Post by tottenham12712 on 2011-07-23
ok thanks :) im going to look into the gateway as it was access a few hours before I went into work....good thing logs were invented. hopefully that leads me somewhere, ill keep you updated!

Thanks again

---

### Post by tottenham12712 on 2011-07-24
bump, still having an issue :(

---

### Post by kuttya on 2011-10-22
if you want to ping your server you can try this site. [WhoisXY.com]("http://www.whoisxy.com/ping.aspx")

---

