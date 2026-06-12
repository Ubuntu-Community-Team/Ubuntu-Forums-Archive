---
title: "can't access Ubuntu server from the internet"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by hockman5 on 2009-01-11
I am running Ubuntu Server 8.10 which is a mail server and a webserver. Everything is working great and has been for about a week. I use dyndns.com as a DNS host to point my domain name to my server. As of yesterday, my domain name no longer redirects to my server. I checked the dyndns site and everything, including the ip, is correct. When i use the local ip of the box from another connected PC, all the services are accessible, Just can't access them from the internet anymore useing domain name or public ip. No settings have changed on the router or the server so I don't understand why this would just stop working all of a sudden. Please let me know if you have ideas.
Thanks

:guitar:

---

### Post by felker2 on 2009-01-11
> **hockman5 said:**
> I am running Ubuntu Server 8.10 which is a mail server and a webserver. Everything is working great and has been for about a week. I use dyndns.com as a DNS host to point my domain name to my server. As of yesterday, my domain name no longer redirects to my server. I checked the dyndns site and everything, including the ip, is correct. When i use the local ip of the box from another connected PC, all the services are accessible, Just can't access them from the internet anymore useing domain name or public ip. No settings have changed on the router or the server so I don't understand why this would just stop working all of a sudden. Please let me know if you have ideas.
Thanks

:guitar:

What is the (error) message you try to access the webserver from a remote point?
Has your server still the same internal IP address? 
Is your router/NAT still forwarding to the correct internal IP address?
You could check [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

BTW: A nice moment for me to plug IPv6 ... "sudo apt-get install miredo" will give you IPv6 connectivity. With IPv6 you have no NAT problems.

---

### Post by HermanAB on 2009-01-11
What do you get when you do a DNS test:
$ dig server.example.com

or
$ nslookup server.example.com


BTW, typically a business server account with your ISP only costs about $10 per month more with two fixed IP addresses and you will get faster access to boot. DynDNS isn't really worth the head-ache.

Cheers,

Herman

---

### Post by hockman5 on 2009-01-11
> **HermanAB said:**
> What do you get when you do a DNS test:
$ dig server.example.com

or
$ nslookup server.example.com


BTW, typically a business server account with your ISP only costs about $10 per month more with two fixed IP addresses and you will get faster access to boot. DynDNS isn't really worth the head-ache.

Cheers,

Herman

I have used DynDNS for years and never had a problem with it.
Here is my output from dig. It is working fine, that is what I can't figure out.
mike@myserver:~$ dig [www.google.com](www.google.com)

; <<>> DiG 9.5.0-P2 <<>> [www.google.com](www.google.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 6635
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 7, ADDITIONAL: 7

;; QUESTION SECTION:
;[www.google.com](www.google.com).			IN	A

;; ANSWER SECTION:
[www.google.com](www.google.com).		532980	IN	CNAME	[www.l.google.com](www.l.google.com).
[www.l.google.com](www.l.google.com).	92	IN	A	74.125.95.104
[www.l.google.com](www.l.google.com).	92	IN	A	74.125.95.147
[www.l.google.com](www.l.google.com).	92	IN	A	74.125.95.103
[www.l.google.com](www.l.google.com).	92	IN	A	74.125.95.99

;; AUTHORITY SECTION:
l.google.com.		49627	IN	NS	b.l.google.com.
l.google.com.		49627	IN	NS	f.l.google.com.
l.google.com.		49627	IN	NS	d.l.google.com.
l.google.com.		49627	IN	NS	c.l.google.com.
l.google.com.		49627	IN	NS	a.l.google.com.
l.google.com.		49627	IN	NS	g.l.google.com.
l.google.com.		49627	IN	NS	e.l.google.com.

;; ADDITIONAL SECTION:
f.l.google.com.		85929	IN	A	72.14.235.9
b.l.google.com.		81994	IN	A	74.125.45.9
c.l.google.com.		83604	IN	A	64.233.161.9
e.l.google.com.		80716	IN	A	209.85.137.9
g.l.google.com.		83604	IN	A	74.125.95.9
d.l.google.com.		85929	IN	A	66.249.93.9
a.l.google.com.		85929	IN	A	209.85.139.9

;; Query time: 105 msec
;; SERVER: 76.85.229.110#53(76.85.229.110)
;; WHEN: Sun Jan 11 16:15:08 2009
;; MSG SIZE  rcvd: 340

---

### Post by hockman5 on 2009-01-11
When I dig my server I get this....

mike@myserver:~$ dig [www.myserver.com](www.myserver.com)

; <<>> DiG 9.5.0-P2 <<>> [www.myserver.com](www.myserver.com)
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 51650
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 5, ADDITIONAL: 4

;; QUESTION SECTION:
;[www.myserver.com](www.myserver.com).		IN	A

;; ANSWER SECTION:
[www.myserver.com](www.myserver.com).	43200	IN	CNAME	myserver.com.
myserver.com.		60	IN	A	##.##.###.### (my correct ip#)

;; AUTHORITY SECTION:
myserver.com.		86400	IN	NS	ns4.mydyndns.org.
myserver.com.		86400	IN	NS	ns3.mydyndns.org.
myserver.com.		86400	IN	NS	ns2.mydyndns.org.
myserver.com.		86400	IN	NS	ns1.mydyndns.org.
myserver.com.		86400	IN	NS	ns5.mydyndns.org.

;; ADDITIONAL SECTION:
ns1.mydyndns.org.	85310	IN	A	63.208.196.92
ns2.mydyndns.org.	82528	IN	A	204.13.249.76
ns4.mydyndns.org.	85193	IN	A	91.198.22.76
ns3.mydyndns.org.	77335	IN	A	208.78.69.76

;; Query time: 307 msec
;; SERVER: 76.85.229.110#53(76.85.229.110)(don't know who's ip this is)
;; WHEN: Sun Jan 11 16:23:00 2009
;; MSG SIZE  rcvd: 231

---

### Post by albinootje on 2009-01-11
> **felker2 said:**
>  Has your server still the same internal IP address? 
Is your router/NAT still forwarding to the correct internal IP address?
You could check [http://portforward.com/routers.htm](http://portforward.com/routers.htm)


To the OP, you should really double-check whether your server has the same ip-address, and whether your port_forwarding still works OK on your router.

If you've connected successfully from within your LAN to the *same* ip-address as before, it really sounds like a port_forwarding problem.

Concerning flaky DSL-modems.. I've seen a DSL-modem which would randomly *close* open ports, and make traffic impossible, and happily opening them randomly later on.
The previous sysadmin actually phoned the ISP a while back, and they (ISP-helpdesk) said they knew about the problems with those DLS-modems

---

### Post by hockman5 on 2009-01-11
> **felker2 said:**
> What is the (error) message you try to access the webserver from a remote point? From an internet browser to my domain name I get....Cannot find server.

Has your server still the same internal IP address? Yes
Is your router/NAT still forwarding to the correct internal IP address?YES
You could check [http://portforward.com/routers.htm](http://portforward.com/routers.htm)

BTW: A nice moment for me to plug IPv6 ... "sudo apt-get install miredo" will give you IPv6 connectivity. With IPv6 you have no NAT problems.
I dont understand how that would fix this problem....

---

### Post by hockman5 on 2009-01-11
> **albinootje said:**
> To the OP, you should really double-check whether your server has the same ip-address, and whether your port_forwarding still works OK on your router.

If you've connected successfully from within your LAN to the *same* ip-address as before, it really sounds like a port_forwarding problem.

Concerning flaky DSL-modems.. I've seen a DSL-modem which would randomly *close* open ports, and make traffic impossible, and happily opening them randomly later on.
The previous sysadmin actually phoned the ISP a while back, and they (ISP-helpdesk) said they knew about the problems with those DLS-modems

The weird part of this is that incoming mail still gets sent to the server via the @myserver.com address. I can not retrieve my mail like i could yesterday, using outlook POP and directing it to the same server name. Now I have to use the local IP address from within a local computer connected to the same router.
Also the DIG command seems to be directing it to the server as well. I can not ssh to the server name. I can't telnet any ports.
I can ping the server with [www.servername.com](www.servername.com). (weird)
I can access web sites from a browser on the server just fine. It seems like it might be a router problem though the settings haven't changed and everything looks like it was before. I will try to erase all the port fowarding and set it up again and see if that helps. And BTW it is a cable modem.

---

### Post by hockman5 on 2009-01-11
OK i removed all port forwarding and saved the router. Then I reentered them again. I powered off the router and power it on again. I can ping my domain name but that is as far as I can get.
No ports being forwarded. Maybe this is a firewall issue? I am pretty sure my firewall is disabled. How can I troubleshoot that?

---

### Post by felker2 on 2009-01-12
> **hockman5 said:**
> I dont understand how that would fix this problem....

Well, because IPv6 does not need NAT, and I'm quite sure the root cause here is a NAT problem.

So if you "sudo apt-get install miredo" and "ifconfig" then shows a 2001:-address, it's easy to check whether your server is reachable at all. If you do this and give us the 2001:, we can check for you.

---

### Post by felker2 on 2009-01-12
> **hockman5 said:**
> 
I can ping the server with [www.servername.com](www.servername.com). (weird)


That's probably your (or someone else's) modem pinging back, not your server.

---

### Post by felker2 on 2009-01-12
> **hockman5 said:**
> 
From an internet browser to my domain name I get....Cannot find server.


Which internet browser are you using?
Do you get the error message immediately, of after a few seconds?
What URL are you using?
From where are you trying to access your webserver? From a client on your LAN, or from the outside world / Internet?
Is the IP address reported back to you by [http://whatsmyip.org/](http://whatsmyip.org/) the same as you have in your dyndns?
What if you use a URL with your own public IP address like [http://11.22.33.44/](http://11.22.33.44/)


BTW: you don't make it easier for us by not telling your domain nor IP address.

---

### Post by felker2 on 2009-01-12
> **hockman5 said:**
> 
;; SERVER: 76.85.229.110#53(76.85.229.110)(don't know who's ip this is)


Well, easy to see:

```
sander@flappie:~$ host 76.85.229.110
110.229.85.76.in-addr.arpa domain name pointer dns-redirect-lb-01.peakview.rr.com.
sander@flappie:~$
```

So it's DNS server from rr.com / Road Runner. It's the DNS server you're using. I guess RoadRunner is your ISP.

---

### Post by felker2 on 2009-01-12
@OP:

On the machine acting as webserver, start up Firefox, and report what you get when you access [http://www.utorrent.com/testport.php?port=80](http://www.utorrent.com/testport.php?port=80)

If it says "Error! Port 80 does not appear to be open.", the problem is a pure NAT/IP/Firewall thing, and not DNS related. You then need to check NAT and IP, and don't need to look at dyndns and dig etc.

---

### Post by hockman5 on 2009-01-12
Well this morning everything worked fine without any changes. Apparantly it was some kind of fluke that fixed itself. Hope it doesn't happen again or often. Thanks for your suggestions.

---

