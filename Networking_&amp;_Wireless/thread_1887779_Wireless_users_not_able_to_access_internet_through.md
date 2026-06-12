---
title: "Wireless users not able to access internet through squid proxy"
date: 2011-11-27
forum: Networking &amp; Wireless
---

### Post by ananthkadalur on 2011-11-27
Hi..everybody
I am using ubuntu 11.04 and I could successfully configured transparent proxy using [this]("http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html") link.  Everything is working fine for only those users who are using wired  connection. DNS and DHCP servers also is configured in the same proxy  server. Here is the server setup details.
```
eth0=192.168.1.2/24(Internet)
gateway=192.168.1.1

eth1=192.168.0.1/24(LAN)

DHCP range 192.168.0.200-192.168.0.254
```The forward IP is mentioned in /etc/bind/named.conf.options file as
```
forwarders {
    192.168.1.1;
    };
``````
cat /etc/resolv.conf 
seach ourdomain_name.com.
nameserver 192.168.0.1
```The wired clients are able to ping internal and external domains. And  mailclients, FTP, and everything is working fine for wired users who are  in the 192.168.0.0 range.

Now I'll come to wireless network
```
wireless router details
IP 192.168.0.236/24
g/w 192.168.0.1
dns 192.168.0.1
dhcp range 192.168.1.200 192.168.1.254
```The wireless users who are in 192.168.1.0 network are neither able to  ping 192.168.0.1 nor external domains. But if they go without proxy then  the wireless details will be same and the internet will be working fine for the wireless users. At that time the setup will be as below
```
Internet--->Cisco load balancer192.168.0.1(DHCP range 192.168.0.200 to 192.168.0.254)--->Wireless router with the same above IP and DHCP range.
```Then I thought, may be I need to route 192.168.1.0 network and ran
```
route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.0.1 dev eth1
```command from the proxy server. Now all the users who comes in  192.168.1.0 network and also 192.168.0.0 network users are able to ping  192.168.0.1 and also some other internal domains but not to external  domains. Then I checked from the server, now from the server also  neither able to ping nor nslookup to external domains. Then I deleted  the entry using

```
route del -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.0.1 dev eth1
```command and found the internet is working fine for only 192.168.0.0 network users who are using wired connection.
So please help me in find out where I am wrong.

---

### Post by MGUbunt on 2011-12-20
Did you solve this?

I have a simila issu

---

