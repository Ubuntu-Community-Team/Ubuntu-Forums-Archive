---
title: "router can't see ubuntu with static ip"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by walter_j on 2009-01-23
I set up a ubuntu server with a ip address of 192.168.0.99. Ifconfig confirms the ip. I set up the router (Dlink EBR 2310) so the DHCP range is from 192.168.0.100 to 192.168.0.199. I set up a DMZ host in the router for the server but could not connect via ssh or through the web browser. I also tried port forwarding and virtual server, but that didn't work either. Everything just times out. I can ping the router's public address. It's as if the router does not see the server with the static ip. When I view the status of the router it lists all pc's except the server.

Is there a setting in ubuntu that prevents it from being seen by the router?

---

### Post by nishv on 2009-01-23
It looks like it is conflicting with the DHCP allocation...

Can you ping the router from the server?

Also, Can you check the netstat -r output?

---

### Post by walter_j on 2009-01-23
I can't ping the router's public ip.

netstat -r gives
destination = 192.168.0.0
gateway = *
genmask = 255.255.255.0
Flags U
MSS 0
window 0
\irtt 0
Iface eth0

---

### Post by Iowan on 2009-01-23
The netstat results look a little sparse. Is there a "default" line - or a line with a "UG" flag?

---

### Post by walter_j on 2009-01-23
> **Iowan said:**
> The netstat results look a little sparse. Is there a "default" line - or a line with a "UG" flag?

There's no defaul line. nothing with flag UG

---

### Post by Cosimix on 2009-01-23
Please send all the output of the following: 
ifconfig -a
route -n
arp -n
sudo iptables -nvL

---

### Post by walter_j on 2009-01-24
> **Cosimix said:**
> Please send all the output of the following: 
ifconfig -a
route -n
arp -n
sudo iptables -nvL

iptables give me unknown command.

---

### Post by Iowan on 2009-01-24
Try adding the following to your /etc/network/interfaces definition for your interface:```
gateway 192.168.0.1     
dns-nameservers 192.168.0.1
```This assumes your router is at 192.168.0.1.

---

### Post by Cosimix on 2009-01-25
yep. Your problem is default gw is missing, if you can't resolve also addresses is missing dns settings. Also there is one host in arp table 192.168.0.105 I guess it might be your router??

If you have enabled DHCP on the router why dont you use it? 

Enable automatic configuration using dhcp client 
[B]sudo nano /etc/network/interfaces
[/B]
[B]auto eth0
iface eth0 inet dhcp
[/B] 
or for static settings:

ASSUMING YOUR ROUTER IS 192.168.0.1 do the following:
[B]auto eth0
 iface eth0 inet static
address 192.168.0.99
netmask 255.255.255.0
gateway 192.168.0.1
network 192.168.0.0
broadcast 192.168.0.255

[/B]and edit dns settings in /etc/resolv.conf
**nameserver 192.168.0.1**


and** sudo /etc/init.d/networking restart**
to apply the configuration


[COLOR=Blue]"I set up a DMZ host in the router for the server but could not connect via ssh or through the web browser."

[COLOR=Black]connectivity:[/COLOR]
[COLOR=Black][B]ping 192.168.0.1
[/B]
http test - see if you can open a connection:
[/COLOR][B][COLOR=Black]telnet 192.168.0.1 80

[/COLOR][/B][COLOR=Black]https test[/COLOR][B][COLOR=Black]
[/COLOR][/B][/COLOR][COLOR=Blue][B][COLOR=Black]telnet 192.168.0.1 443
[/COLOR][/B][/COLOR][COLOR=Blue][COLOR=Black]if the latter can open a connection you need to use "https://" in the web browser

****Most services like http https ssh telnet needs enabling on the router - check user manual*** 


[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]dns resolving test:
[/COLOR]**[COLOR=Black]nslookup google.com[/COLOR]**[/COLOR]
[B]
ping google.com[/B]
a way to verify if internet access is ok

---

### Post by Cosimix on 2009-01-25
Id change the thread title to "UBUNTU HOWTO Configuring gateway"

---

### Post by walter_j on 2009-01-25
I'll try this monday am. I would use the router dhcp but i need a static ip to ssh to the ubuntu server. Apparently the router can also port forward by pc name, so maybe I don't really need a static ip if this is the case.

---

### Post by walter_j on 2009-01-26
Worked great. Thanks everyone.

---

### Post by Cosimix on 2009-02-09
I am glad to be helpful sometimes

---

