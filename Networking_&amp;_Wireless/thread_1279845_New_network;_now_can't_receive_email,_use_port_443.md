---
title: "New network; now can't receive email, use port 443, etc"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by standards on 2009-10-01
So I just set up my box in a new building and have a wired connection to a hub (which itself is connected from another building I don't have access to). 

Suddenly I am unable to download new emails (it times out. can SEND emails fine) and software I use that requires port 443 (HTTPS) doesn't connect. 

Looking up my IP address and nmapping it, I get this:

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-10-01 11:26 EDT
Interesting ports on xxx (70.183.165.xx):
Not shown: 985 filtered ports
PORT      STATE  SERVICE
20/tcp    closed ftp-data
21/tcp    closed ftp
22/tcp    open   ssh
23/tcp    closed telnet
25/tcp    closed smtp
37/tcp    open   time
43/tcp    closed whois
53/tcp    closed domain
80/tcp    closed http
109/tcp   closed pop2
110/tcp   closed pop3
143/tcp   closed imap
443/tcp   closed https
6667/tcp  closed irc
10000/tcp closed snet-sensor-mgmt

but I am able to use websites (e.g. my bank) that require HTTPS so I'm sort of lost. I'm told there may be a "firewall" operating somewhere but the funny thing is that everything works normally on my laptop when it is connected wirelessly to the same network, so I figure there must be some setting somewhere I am missing or I don't know? This is a little beyond my understanding. 

Previously I was just directly connected to my own cable modem.

Thanks in advance..

---

