---
title: "Squid not working"
date: 2012-11-15
forum: Networking &amp; Wireless
---

### Post by intelaravind on 2012-11-15
Hi,

I have setup a squid proxy server in ubuntu (I am new to this). The configuration is as given below. The aim is to **allow** torrents through this proxy. I have given the proxy server as http, and given correct port and server address in the torrent client (qBittorent).

I saw of a couple of TCP_MISS/503 in the access.log. But the thing is, it is updated again and again (it should right as the torrent is trying to connect again and again)

One more thing is I am not sure whether there is a problem in allowed network configuration. One of my network ip is 130.79.192.146 and the mask is 255.255.255.128.

```
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
acl our_networks src 130.79.192.0/24
http_access allow our_networks
http_access allow !Safe_ports
http_access allow CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_port 3128
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .		0	20%	4320

```

Any help is appreciated.

---

