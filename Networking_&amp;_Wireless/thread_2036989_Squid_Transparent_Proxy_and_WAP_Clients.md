---
title: "Squid Transparent Proxy and WAP Clients"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by sixstorm on 2012-08-03
I finally got my Squid box to work as a transparent proxy but noticed that anyone that connects to the WAP cannot go anywhere; it basically times out and does not show a "blocked" page reply.  All settings from my DHCP server come through just fine, say on my laptop or phone, and the WAP is set to use my Squid box as the gateway.  The funny thing is that any wired device works just fine and I don't see ANY traffic coming from wireless devices in my access.log.

In my Squid config, I have our LAN defined with the entire scope that is allowed http access.  

Anybody ever seen this?  I'm sure it's something stupid and I can't put my finger on it.  Help!  :confused:

EDIT:  Here is my Squid.conf:

```
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 443		# https
acl CONNECT method CONNECT
acl badtemp url_regex "/etc/squid3/block.acl"
acl video url_regex "/etc/squid3/videosites.acl"
acl alwaysblock url_regex "/etc/squid3/alwaysblock.acl"
acl morning1 time MTWHF 6:00-8:00
acl morning2 time MTWHF 9:30-9:45
acl lunch time MTWHF 11:30-12:00
acl citclass_network src 172.28.1.0/16
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny alwaysblock
http_access deny video
http_access deny badtemp !lunch
http_access allow badtemp lunch
http_access deny badtemp !morning1
http_access allow badtemp morning1
http_access deny badtemp !morning2
http_access allow badtemp morning2
http_access allow citclass_network
http_access deny all
http_port 8888 transparent
cache_mem 1024 MB
cache_dir ufs /var/spool/squid3 100 16 256
refresh_pattern -i \.(gif|png|jpg|jpeg|ico|bmp)$ 260000 90% 260009 override-expire
log_fqdn on
```

---

### Post by sixstorm on 2012-08-04
Bump.  Any clue to this mystery?

---

### Post by sixstorm on 2012-08-06
Bump again.  

I had a student to connect to the WAP, input manual IP address and settings, and he was able to get out to the Internet with no problem.  I've checked time and time again with DHCP settings and all settings come through just fine.  Puzzled!  :confused:

---

### Post by SeijiSensei on 2012-08-06
If you're running a transparent proxy, you presumably are using an iptables PREROUTING rule.  It sounds to me like the rule doesn't include connections via WAP.  If, as you say, you can use the proxy by manually including the address and port number, then I'd look to the iptables rule as the source of the problem.

---

### Post by sixstorm on 2012-08-06
> **SeijiSensei said:**
> If you're running a transparent proxy, you presumably are using an iptables PREROUTING rule.  It sounds to me like the rule doesn't include connections via WAP.  If, as you say, you can use the proxy by manually including the address and port number, then I'd look to the iptables rule as the source of the problem.

I used the IPTABLES rule that you posted in my other thread regarding using a transparent proxy, but included the entire subnet that we are running on.  It makes sense when looking at the rule but I'm not sure why web traffic isn't passing through.  Any other clues?  I'm going to look at all IPTABLES rules to make sure nothing else is blocking it.

---

### Post by sixstorm on 2012-08-06
Ran iptables -L and I don't see any rules, however I know that the one rule below is working as everyone in my class is going through the squid box.

```
iptables -t nat -A PREROUTING -p tcp -j REDIRECT --to-port 3128 -s 192.168.1.0/24 --destination-port 80
```

---

### Post by sixstorm on 2012-08-07
Found the issue.  We are running on a /16 subnet in the class (not my choice but whatever) and my IPTABLES rule stated for /16.  I not only reinput the command for the /16 subnet but also did it for /24.  Not sure what happened but all WAP clients can now get to the web.

Going to reboot and see if the reboot kills those IPTABLES rules.

Thanks again for the help SeijiSensei.

---

