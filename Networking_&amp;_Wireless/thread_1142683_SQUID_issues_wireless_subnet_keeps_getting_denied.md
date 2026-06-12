---
title: "SQUID issues wireless subnet keeps getting denied"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by commlord on 2009-04-29
Hello,
I have no idea what else to check and have scoured the net for a solution.
I have a dedicated ubuntu 8.1 running squid 2.7 in a dmz.  the firewall is forwarding all the web traffic via the proxy.
My main subnet works fine. I have multiple subnets for wireless clients. one public and one private that has access back to the LAN.  No other subnets work.

Anyway, the public wireless subnet gets denied at the proxy no matter what i enter in the config.  with Squid stopped the subnet routes fine to the internet, so i am assuming its not rules on the firewall between zones.
log error:  192.168.11.18 TCP_DENIED/400 2016 GET error:invalid-request - NONE/- text/html



Here is my squid.conf:
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl to_localhost dst 127.0.0.0/8
acl localnet src 10.0.0.0/24	# (this is my main subnet, working)
acl publicaccess src 192.168.10.0/255.255.255.0 

acl wirelesspublic src 192.168.11.0/255.255.255.0 ##(this is the problem subnets)  i have tried with the /24 and it didnt matter.

acl wirelessemp src 10.1.1.0/255.255.255.0

acl SSL_ports port 443		# https
acl SSL_ports port 563		# snews
acl SSL_ports port 873		# rsync
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
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny to_localhost
http_access allow localnet
http_access allow localhost
http_access allow wirelesspublic
http_access allow wirelessemp
http_access allow publicaccess
http_access deny all
icp_access allow localnet
icp_access allow wirelesspublic
icp_access allow wirelessemp
icp_access allow publicaccess
icp_access deny all
http_port 8888
hierarchy_stoplist cgi-bin ?
access_log /var/log/squid/access.log squid
logfile_rotate 9
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
extension_methods REPORT MERGE MKACTIVITY CHECKOUT
visible_hostname proxy1
hosts_file /etc/hosts
coredump_dir /var/spool/squid


Any suggestions as i am out of ideas.  I have tried to specifically isolate one IP and that didnt work either.

-- Marc

---

### Post by commlord on 2009-04-30
any thoughts on this or someplace else to post?

thanks,

---

