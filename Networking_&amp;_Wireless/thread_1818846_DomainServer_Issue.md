---
title: "Domain/Server Issue"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by computerfox on 2011-08-05
Hello Everyone,

So I'm having an issue here:

foxwebhosting.dyndns.org ->DNS, set up via IP
foxwebhosting.dyndns.org -> DNS, set up via IP and virtual server

Now for the main issue:

foxhowto.com -ns1: foxwebhosting  ns2: foxwebhosting2


Now, I have webmin for the control panel and I was able to set up multiple servers before, I just haven't set up a server in a few months and just forgot.  The browser says that it can't find the server.  Is this just an issue that the registrar hasn't finished updating the dns or do i have a big problem here?

Any help would be greatly appreciated.

---

### Post by computerfox on 2011-08-05
Anyone?

---

### Post by Boondoklife on 2011-08-05
How long ago did you put in the request for the dns? it can take upto 72 hrs in some case.

---

### Post by computerfox on 2011-08-06
> **Boondoklife said:**
> How long ago did you put in the request for the dns? it can take upto 72 hrs in some case.

Thank you for the response, but here's what I have so far:

foxwebhosting.dyndns.org and foxwebhosting2.dyndns.org->have the same IP on dyndns.org

registrar->^

Both of those work, just not my virtual server at foxhowto.com

Any ideas?

---

### Post by SoftwareExplorer on 2011-08-06
Ok, so the .com servers are saying that foxhowto.com is controlled by foxwebhosting.dyndns.org and foxwebhosting2.dyndns.org. However, when my computer tried to connect to a DNS server on foxwebhosting.dyndns.org  to ask what address foxhowto.com is at, it couldn't connect to a DNS server on foxwebhosting.dyndns.org. I tried running a portscan, and here's what it said: ```
nmap foxwebhosting.dyndns.org

Starting Nmap 5.21 ( http://nmap.org ) at 2011-08-06 11:36 PDT
Nmap scan report for foxwebhosting.dyndns.org (173.70.120.83)
Host is up (0.17s latency).
rDNS record for 173.70.120.83: pool-173-70-120-83.nwrknj.fios.verizon.net
Not shown: 996 filtered ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
666/tcp  open  doom
4567/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 13.57 seconds

```
If you had a DNS server working, it should have had a line that said something like "53/tcp open  domain". So it appears that one of two things could be happening: first, your DNS server could be plain old not running. Second, it could be running, but a firewall could be blocking port 53/tcp incoming, firewalling the world from connecting to it.

---

### Post by computerfox on 2011-08-06
> **SoftwareExplorer said:**
> Ok, so the .com servers are saying that foxhowto.com is controlled by foxwebhosting.dyndns.org and foxwebhosting2.dyndns.org. However, when my computer tried to connect to a DNS server on foxwebhosting.dyndns.org  to ask what address foxhowto.com is at, it couldn't connect to a DNS server on foxwebhosting.dyndns.org. I tried running a portscan, and here's what it said: ```
nmap foxwebhosting.dyndns.org

Starting Nmap 5.21 ( http://nmap.org ) at 2011-08-06 11:36 PDT
Nmap scan report for foxwebhosting.dyndns.org (173.70.120.83)
Host is up (0.17s latency).
rDNS record for 173.70.120.83: pool-173-70-120-83.nwrknj.fios.verizon.net
Not shown: 996 filtered ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
666/tcp  open  doom
4567/tcp open  unknown

Nmap done: 1 IP address (1 host up) scanned in 13.57 seconds

```
If you had a DNS server working, it should have had a line that said something like "53/tcp open  domain". So it appears that one of two things could be happening: first, your DNS server could be plain old not running. Second, it could be running, but a firewall could be blocking port 53/tcp incoming, firewalling the world from connecting to it.


Thanks Explorer.  I took a look at what you mentioned and I changed a few things.  I took snapshots just to make sure.

---

### Post by computerfox on 2011-08-06
i'm probably not doing something that's small X_X

---

### Post by computerfox on 2011-08-06
Anything?

---

### Post by computerfox on 2011-08-07
i took another look at my configuration and everything was mixed up.  i think i figured it out, but since i stupidly changed my dns on the registrar, i now have to wait about 2 hours before i can change it to test my hypothesis. unless me doing a dns on zonomi completely screwed me over...

---

### Post by SoftwareExplorer on 2011-08-07
I'm able to load it from here with no problem. So the problem is fixed, or at least it will be once various DNS servers quit remembering the old information and load the new information.

---

### Post by computerfox on 2011-08-07
> **SoftwareExplorer said:**
> I'm able to load it from here with no problem. So the problem is fixed, or at least it will be once various DNS servers quit remembering the old information and load the new information.

Well yes and no. It's still set uP with the other dns provider. I want to use my own. :-(

---

### Post by computerfox on 2011-08-08
i guess i'm just going to bite the bullet and use that free dns service in relation to one of mine.  at least then it would work :-)

---

### Post by SoftwareExplorer on 2011-08-08
Sorry it took a while for me to reply. 

A good idea would be to stick with the free provider until you get yours working. Then you could switch which server is listed as the authority for foxhowto.com without any downtime.

My guess is that you have the name server running, but your firewall is blocking it. I think this because you have screenshots of settings for the DNS servers. Check to make sure that your firewall is letting port 53 be open to the outside world. Also, you might try running ```
ps aux| grep -P "[n]amed"
``` and post the result to see if it is actually running.

---

