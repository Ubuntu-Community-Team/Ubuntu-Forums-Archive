---
title: "using ssh to connect to computers"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by ajb359 on 2011-07-13
Hey I initially posted this in the General forum and thought I give it a shot here.
"""
I am new (not only to the forums but ubuntu) so sorry if this is in the  wrong area. I want to be able to access my desktop from work so I first  set up a DNS. I can ssh into my own computer and using the ip address  but when I try to ssh using my DNS (this is from my home wireless which  is Linksys E2000), I get the following error:

debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to ****.com [74.79.145.28] port 50000
debug1: Connection established.
debug1: identity file /home/andy/.ssh/id_rsa type -1
debug1: identity file /home/andy/.ssh/id_rsa-cert type -1
debug1: identity file /home/andy/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: identity file /home/andy/.ssh/id_dsa-cert type -1
debug1: identity file /home/andy/.ssh/id_ecdsa type -1
debug1: identity file /home/andy/.ssh/id_ecdsa-cert type -1
debug1: ssh_exchange_identification: HTTP/1.1 400 Bad Request


debug1: ssh_exchange_identification: Server: httpd


debug1: ssh_exchange_identification: Date: Tue, 12 Jul 2011 22:06:15 GMT


debug1: ssh_exchange_identification: Content-Type: text/html


debug1: ssh_exchange_identification: Connection: close


debug1: ssh_exchange_identification: 


debug1: ssh_exchange_identification: <HTML><HEAD><TITLE>400 Bad Request</TITLE></HEAD>

debug1: ssh_exchange_identification: <BODY BGCOLOR="#cc9999"><H4>400 Bad Request</H4>

debug1: ssh_exchange_identification: No request found.

debug1: ssh_exchange_identification: </BODY></HTML>

ssh_exchange_identification: Connection closed by remote host

I set up the settings on the Linksys to accept DDNS but I am thinking  there might be something else I overlooked? I do not understand  completely what is happening to debug this. It seems like it initially  accepts the connection and then something strange occurs. Does anyone  have any ideas? Thanks!
"""

---

### Post by Jake.Debord on 2011-07-13
Port 50000? Do you know what port SSH listens to on your server? You may need to redirect port 50000 to 22 on your router

---

