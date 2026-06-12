---
title: "Simple SQUID HTTP Proxy server - Connection refused"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by Ludalex on 2012-12-17
Hello, I'm trying to setup a basic Squid3 proxy server to redirect http requestes made from a PHP script from another server.

I just installed Ubuntu 12.04 on this Australian VPS and installed squid3 right away. 

With  configuration below I always get "Connection refused" connecting from my PC in another country (with Firefox and a cURL script), even tough I have set to allow all http traffic.

What's wrong with it?

```
http_port 80 (-- ALSO TRIED 3128, DOESN'T WORK)
visibile_hostname n4checker

refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern .               0       20%     4320

acl localnet src 10.0.0.0/8     # RFC 1918 possible internal network
acl localnet src 172.16.0.0/12  # RFC 1918 possible internal network
acl localnet src 192.168.0.0/16 # RFC 1918 possible internal network
acl localnet src fc00::/7       # RFC 4193 local private network range
acl localnet src fe80::/10      # RFC 4291 link-local (directly plugged) machines
acl localhost src 127.0.0.1

acl home src 62.98.3.194/255.255.255.255

acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT

http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access allow home
http_access allow localhost
http_access allow all

```

---

### Post by SeijiSensei on 2012-12-17
Do you have a firewall?  Is it configured to allow access from the machine running the PHP script?  Is the PHP script configured to use a proxy?

Put squid back on 3128 and make sure that the script machine can see that port.  Try "telnet squid_host 3128".  What happens?

---

### Post by Ludalex on 2012-12-17
> **SeijiSensei said:**
> Do you have a firewall?  Is it configured to allow access from the machine running the PHP script?  Is the PHP script configured to use a proxy?

Put squid back on 3128 and make sure that the script machine can see that port.  Try "telnet squid_host 3128".  What happens?

I don't have a firewall since I just installed the server. The PHP script works fine with other proxies (HTTP or SOCKS ones) and as second test I always try to connect to the proxy with Firefox.

The telnet command unfortunately gives me this:
> vps@n4checker:~$ telnet n4checker 3128
Trying 103.1.186.146...
telnet: Unable to connect to remote host: Connection refused

Thanks for your help.

---

### Post by SeijiSensei on 2012-12-18
Is 62.98.3.194/255.255.255.255 the IP of the machine trying to connect?

I added a dst ACL to a squid host today and when I restarted squid bitched about the netmask.  Squid prefers CIDR notation now.  Try replacing the address above with 62.98.3.194/32 and see if that makes a difference.

What do you see in the squid logs when you try to connect?  Is there a browser on the machine running squid?  Configure it to use the proxy via 127.0.0.1 and make sure it works that way.  If you don't have a GUI installed, use elinks.  You can also try just running "telnet localhost 3128" and see if the cache replies.

---

