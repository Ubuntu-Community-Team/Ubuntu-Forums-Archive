---
title: "network issue"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by 696f6e6963 on 2009-07-14
I was just given a Ubuntu 9.04 server to work on. I can only ping localhost, my IP, and my DNS server. I cannot ping any other host or ip address on the network or outside the network. I am given "ping: unknown host <hostname>". Moreover, I cannot do an apt-get update/upgrade/install. 
> Failed to fetch [http://security.ubuntu.com/path/file](http://security.ubuntu.com/path/file). Could not resolve "security.ubuntu.com"
Some of the files failed to download, they have been ignored, or old ones used instead.
You may want to run apt-get update to correct these problems.

The server is pingable from other hosts on the network and a webserver is running and is accessable. I disabled ufs. Firestarter nor CSF is installed (I'm not sure if there is another firewall installed since the guy who set up the server is MIA). It seems like all outbound connections are being blocked or something. Any ideas whats going on?

---

### Post by 696f6e6963 on 2009-07-14
Could this be an issue with the DNS server itself rather than the Ubuntu install?

---

### Post by cariboo on 2009-07-14
What is the contents of /etc/resolv.conf? Note the spelling of resolv, there is no "e" on the end.

---

### Post by 696f6e6963 on 2009-07-15
search mydomain.com
nameserver 192.168.1.100
nameserver dns_server1
nameserver dns_server2

Where mydomain.com is my actualy domain and dns_server1 and dns_server2 are the ip's of my DNS server

---

### Post by 696f6e6963 on 2009-07-20
This was an issue with websense.

---

