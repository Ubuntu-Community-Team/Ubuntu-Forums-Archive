---
title: "Can ping to outside IP, but not domain"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by oygle on 2009-09-17
Have 2 computers running 9.04 Ubuntu and Firestarter. One computer shares the internet connection, and works fine, but the 'client" computer can only ping to 'outside' IP addresses.

No doubt this is a DNS issue, but the syslogs show no problems ??

Oygle

---

### Post by badger_fruit on 2009-09-17
Did you read this page --> [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

it might help if not.

---

### Post by louigi600 on 2009-09-17
Can you get some traffic trough to/from internet  if you specify ip address instead of hostname ?
Has your pc that is sharing network (let's call it router) a firewall configured ?
Is your router masquerading ?

---

### Post by oygle on 2009-09-17
> **badger_fruit said:**
> Did you read this page --> [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

it might help if not.

Yes, have done all that. That doc has the ethernet interfaces around the wrong way, just a bit confusing (i.e. it has the client and gateway ethernet interfaces named incorrectly, for _that_ example).

Also, the doc could be set out a bit better, to clearly distinguish which commands are for the gateway computer, and which commands are for the client. yes, it does have sub headings, but not real clear and easy to understand.

---

### Post by oygle on 2009-09-17
> **louigi600 said:**
> Can you get some traffic trough to/from internet  if you specify ip address instead of hostname ?

I can ping to a dns server IP address okay from the client computer, so it can ping out to the internet.

> **louigi600 said:**
> 
Has your pc that is sharing network (let's call it router) a firewall configured ?

Yes, both computers have Firestarter.

> **louigi600 said:**
> 
Is your router masquerading ?

The gateway computer (the one doing the ICS), has dnsmasq running.

Oygle

---

### Post by Grenage on 2009-09-17
Assuming you have no internal DNS servers, and that the host computer is the only other machine on the network can't you add a static entry?

Please list your entire setup. Switches, clients, servers and routers etc.

---

### Post by louigi600 on 2009-09-17
By getting some traffic trough I do not mean just ping
try som real tcp traffic like brousing or connecting via telnet or ssh.

For instance cal you get this to work from your ubuntu (liks is text browser):
links [http://199.6.1.164/](http://199.6.1.164/)

If you do not have links try the same url on your normal browser and see if you can get connection to kernel.org. 

Can you show me the output of "iptables-save" on boteh gateway and client ?

Masquerading has nothing to do with dnsmask, the former is a sort of NAT the latter is a smart and compact DNS/dhcp server.
The output of iptables-save will tell me if you are masquerading.

Can you show me the output of "route -n" on bothe client and gateway ?

---

### Post by oygle on 2009-09-17
> **Grenage said:**
> Assuming you have no internal DNS servers, and that the host computer is the only other machine on the network can't you add a static entry?

Both the host (gateway) and the client have static IP's.

> **Grenage said:**
> 
Please list your entire setup. Switches, clients, servers and routers etc.

Internet <==> Host <============>switch <==========> Client

I don't have a hardware router, as I use wireless broadband, the connection is via a USB dongle. Both computers are running Firestarter, and I keep a lookout on the syslos, to see if anything is being blocked. Logs all look okay.

The major 'annoyance' is that I had it all running okay, then people in the security forums told me to drop Firestarter and use UFW, and that's where the problems started. After problems with UFW, I did (completely) remove UFW and re-installed Firestarter.

I have dnsmasq and ipmasq running on the host.

Thanks,

Oygle

---

### Post by oygle on 2009-09-17
> **louigi600 said:**
> For instance cal you get this to work from your ubuntu (liks is text browser):
links [http://199.6.1.164/](http://199.6.1.164/)

Yes, I can do that okay with the client. I also did it for the Google IP, but as soon as I try a domain, ...no go.

> **louigi600 said:**
> 
Can you show me the output of "iptables-save" on boteh gateway and client ?

It didn't like that ..

```

$ iptables -save
iptables v1.4.1.1: no command specified
Try `iptables -h' or 'iptables --help' for more information.

```

Thanks,

Oygle

---

### Post by louigi600 on 2009-09-17
iptables-save is a command all on it's own .... not iptaples -save

Ok the navigation with IP is working ...
then show me the output of
cat /etc/resolv.conf

on bothe client and gateway

---

### Post by Grenage on 2009-09-17
So surely in your current setup you would need to either configure your host machine as a DNS server with an external forward address, or simply use external DNS servers on the client.  I'd do the latter, since you only have one other internal machine.

Try using some from here [http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/) OR use OpenDNS' servers.

Add them to /etc/resolv.conf:

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

---

### Post by oygle on 2009-09-17
> **louigi600 said:**
> 
then show me the output of
cat /etc/resolv.conf

on bothe client and gateway

The gateway had ..

```

# Generated by NetworkManager
nameserver isp.assigned.domainname.server1
nameserver isp.assigned.domainname.server2

```

where "isp.assigned.domainname.server1" and "isp.assigned.domainname.server2" are the dns server IP's of the ISP I use.

On the client, it had exactly the same IP's **BUT**, it didn't have the word "nameserver". I changed that on the client, and now I can browse to a domain, and now have the apt updates going on the client.

Thanks very much, and also many thanks to the others who have helped solve this problem.  :D

Oygle

---

### Post by oygle on 2009-09-17
> **Grenage said:**
> 
Add them to /etc/resolv.conf:

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

Thanks Grenage, that was the problem on the client, it had the IP's, but it didn't have the word 'nameserver'.

Thanks,

Oygle

---

### Post by Grenage on 2009-09-17
Glad to hear that you got it working!

Take care.

---

