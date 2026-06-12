---
title: "who is this host --&gt;192.168.1.253"
date: 2010-12-27
forum: Networking &amp; Wireless
---

### Post by sasa.net on 2010-12-27
hi all :) I'm new on this nice forum and first what I'm gonna do is post a single question about my problem which makes me crazy :/   I have Backtrack 4 R2 installed on my machine... I've started an command multiple times using nmap tool, the command was: nmap 192.168.1.1-255 -Pn my gateway is 192.168.1.1 (by default) my comp has static ip which is 192.168.1.10 (configured in wicd menager) other computers on the LAN network -> it's only one (from my brother) his ip address is dynamic which is 192.168.1.2 (according to to the start pool address 192.168.1.2) as you can see my router is set to -> start pool address 192.168.1.2 and end pool address is set to 192.168.1.10  ok... now after I run this command with nmap tool there are interest result's in output: 192.168.1.1 -> host is up -> my router 192.168.1.2 -> host is up -> my brothers computer 192.168.1.10 -> host is up -> my computer 192.168.1.253 -> host is up unknown  here are details about this host (192.168.1.253)  Nmap scan report for 192.168.1.253 Host is up (0.014s latency) Not shown: 998 filtered ports PORT    STATE  SERVICE 80/tcp  closed http 443/tcp closed https  WHO THE HELL IS THIS HOST ???  I've changed my WPA2 key several times  so nobody can connect to my router just like that but host is steel there (it's up anyway)  can anyone tell me what this address (host) mean I think that's wireless antena maybe ???

---

### Post by VastOne on 2010-12-27
> **sasa.net said:**
> hi all :) I'm new on this nice forum and first what I'm gonna do is post a single question about my problem which makes me crazy :/   I have Backtrack 4 R2 installed on my machine... I've started an command multiple times using nmap tool, the command was: nmap 192.168.1.1-255 -Pn my gateway is 192.168.1.1 (by default) my comp has static ip which is 192.168.1.10 (configured in wicd menager) other computers on the LAN network -> it's only one (from my brother) his ip address is dynamic which is 192.168.1.2 (according to to the start pool address 192.168.1.2) as you can see my router is set to -> start pool address 192.168.1.2 and end pool address is set to 192.168.1.10  ok... now after I run this command with nmap tool there are interest result's in output: 192.168.1.1 -> host is up -> my router 192.168.1.2 -> host is up -> my brothers computer 192.168.1.10 -> host is up -> my computer 192.168.1.253 -> host is up unknown  here are details about this host (192.168.1.253)  Nmap scan report for 192.168.1.253 Host is up (0.014s latency) Not shown: 998 filtered ports PORT    STATE  SERVICE 80/tcp  closed http 443/tcp closed https  WHO THE HELL IS THIS HOST ???  I've changed my WPA2 key several times  so nobody can connect to my router just like that but host is steel there (it's up anyway)  can anyone tell me what this address (host) mean I think that's wireless antena maybe ???

It will be hard to for us to tell who it is inside your network schema, you could use traceback tools to try and get some information...

To prevent anyone from accessing your network could be done in multiple ways... If you want to use DHCP through the router, you could set it to only accept via MAC address or simply limit the number of addresses to the amount of people that will access it but that still leaves an opening when a computer is off.

What I do is eliminate DHCP and go strictly with static IP addresses inside my network.  I also do not use the standard 192.168.1.1, which anyone who has ever used a router knows about..

So switch to a 192.168.xx.1 number as the router address.  Then use static ip's on all machines accessing it.  You could also use a 10.0.0.0 network schema

I will also tell you that I use WICD as I find it a much better Network Manager in Ubuntu.

I know this does not answer your questions but it will eliminate the unknown/illegal access

You can google anyone these suggestions for more information...

---

### Post by hakermania on 2011-01-15
You can also use nmap -O option to detect the Operating System of this person.

---

