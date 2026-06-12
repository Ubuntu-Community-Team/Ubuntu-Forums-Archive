---
title: "Pointing"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by computerfox on 2011-01-24
Hello again.  Now that my server is live, I'm trying to test if I can get it to host other sites.

I created the virtual server
I supposedly have two DNS's with the same address (the physical server)


foxwebhosting.dyndns.org/computerfoxdesign.net works
computerfoxdesign.net does not

Any ideas?

Any help would be greatly appreciated.  Thank you!


FOX

---

### Post by computerfox on 2011-01-25
Can anyone help me with this issue?

---

### Post by computerfox on 2011-01-25
Can someone at least suggest a place where I might be able to find a solution to my problem?

---

### Post by computerfox on 2011-01-25
Attached are pictures of my present state.  Any ideas?  More information is needed?

---

### Post by SoftwareExplorer on 2011-01-25
(I'm assuming that you want different content on each virtualhost. Otherwise, you could make both DNS names point to the same address+virtual server and you'd be done.)
From looking at the screenshots, one of your virtual hosts is set to pick up "any" address. Maybe that virtual host is getting all the requests without giving the 'compufoxwebdesign.net' one a chance to get a request? Maybe if you change the 'any' virtualhost to only have 'foxwebhosting.dyndns.org', then maybe it would work?
Until I did a little research, I thought that Apache wouldn't be able to tell whether a web browser was trying to see compufoxwebdesign.net or foxwebhosting.dyndns.org, because the browser finds out the IP address it needs to use and then connects to the server with it's IP address, leaving the server with no idea what DNS name the browser looked up to find the server's IP address. 
However, according to [[COLOR="DeepSkyBlue"]http://docstore.mik.ua/orelly/linux/apache/ch03_04.htm[/COLOR]]("http://docstore.mik.ua/orelly/linux/apache/ch03_04.htm"), section 3.4.7, if the browser is using the HTTP 1.1 version of the HTTP protocol instead of version 1.0, the browser sends what DNS address it is looking for with it's request and the server can decide what site to give the browser. Now that I've read about it, I may have to try putting two sites on a server with only one IP address.
The page I previously mentioned shows how to set up two virtual servers by editing the configuration files, but you are using something else, so I guess we'll see what we can figure out before resorting to that.

---

### Post by computerfox on 2011-01-25
yeah, i think it's more efficient and cheaper to do it with one server, especially if it's from home.

thank you for catching that and it does sound logical as to why that would be a cause of my problem, but when i changed it, it still wouldn't work.  i checked the registrar and it said that the update was complete.  

any other ideas?  this shouldn't be this hard.

---

### Post by SoftwareExplorer on 2011-01-25
I think I might have found another problem:
(dig is a DNS tool, 'soa' means get me a **S**tart **O**f **A**uthority record which is the DNS record which says which DNS server to ask what the IP address is, '@b.gtld-servers.net' means start by asking one of the root DNS servers, and '+trace' means tell me each time a DNS server says "I don't know, but I do know if you ask <thisOtherDNSserver> they will know")
```
dig soa computerfoxdesign.net @b.gtld-servers.net +trace

; <<>> DiG 9.7.1-P2 <<>> soa computerfoxdesign.net @b.gtld-servers.net +trace
;; global options: +cmd
.                       518400  IN      NS      g.root-servers.net.
.                       518400  IN      NS      h.root-servers.net.
.                       518400  IN      NS      i.root-servers.net.
.                       518400  IN      NS      j.root-servers.net.
.                       518400  IN      NS      k.root-servers.net.
.                       518400  IN      NS      l.root-servers.net.
.                       518400  IN      NS      m.root-servers.net.
.                       518400  IN      NS      a.root-servers.net.
.                       518400  IN      NS      b.root-servers.net.
.                       518400  IN      NS      c.root-servers.net.
.                       518400  IN      NS      d.root-servers.net.
.                       518400  IN      NS      e.root-servers.net.
.                       518400  IN      NS      f.root-servers.net.
;; Received 228 bytes from 2001:503:231d::2:30#53(2001:503:231d::2:30) in 116 ms

net.                    172800  IN      NS      a.gtld-servers.net.
net.                    172800  IN      NS      b.gtld-servers.net.
net.                    172800  IN      NS      c.gtld-servers.net.
net.                    172800  IN      NS      d.gtld-servers.net.
net.                    172800  IN      NS      e.gtld-servers.net.
net.                    172800  IN      NS      f.gtld-servers.net.
net.                    172800  IN      NS      g.gtld-servers.net.
net.                    172800  IN      NS      h.gtld-servers.net.
net.                    172800  IN      NS      i.gtld-servers.net.
net.                    172800  IN      NS      j.gtld-servers.net.
net.                    172800  IN      NS      k.gtld-servers.net.
net.                    172800  IN      NS      l.gtld-servers.net.
net.                    172800  IN      NS      m.gtld-servers.net.
;; Received 499 bytes from 2001:7fd::1#53(k.root-servers.net) in 196 ms

computerfoxdesign.net.  172800  IN      NS      foxwebhosting.dyndns.org.
computerfoxdesign.net.  172800  IN      NS      foxwebhosting2.dyndns.org.
;; Received 106 bytes from 192.26.92.30#53(c.gtld-servers.net) in 142 ms

```
Ok, so I'm supposed to ask the DNS server at foxwebhosting.dyndns.org what the IP address for computerfoxdesign.net is. Let's see what it's IP address is. (this time were asking for an a record, which stands for **A**ddress. If we wanted an IPv6 address record, we would ask for an aaaa record. It's aaaa instead of just 'a' because IPv6 address are 4 times as long as an IPv4 address.)
```
dig a foxwebhosting2.dyndns.org +trace

; <<>> DiG 9.7.1-P2 <<>> a foxwebhosting2.dyndns.org +trace
;; global options: +cmd
.                       82684   IN      NS      b.root-servers.net.
.                       82684   IN      NS      j.root-servers.net.
.                       82684   IN      NS      i.root-servers.net.
.                       82684   IN      NS      m.root-servers.net.
.                       82684   IN      NS      g.root-servers.net.
.                       82684   IN      NS      a.root-servers.net.
.                       82684   IN      NS      e.root-servers.net.
.                       82684   IN      NS      h.root-servers.net.
.                       82684   IN      NS      d.root-servers.net.
.                       82684   IN      NS      c.root-servers.net.
.                       82684   IN      NS      k.root-servers.net.
.                       82684   IN      NS      l.root-servers.net.
.                       82684   IN      NS      f.root-servers.net.
;; Received 497 bytes from 2001:470:20::2#53(2001:470:20::2) in 98 ms

org.                    172800  IN      NS      a0.org.afilias-nst.info.
org.                    172800  IN      NS      a2.org.afilias-nst.info.
org.                    172800  IN      NS      b0.org.afilias-nst.org.
org.                    172800  IN      NS      b2.org.afilias-nst.org.
org.                    172800  IN      NS      c0.org.afilias-nst.info.
org.                    172800  IN      NS      d0.org.afilias-nst.org.
;; Received 448 bytes from 2001:7fd::1#53(k.root-servers.net) in 195 ms

dyndns.org.             86400   IN      NS      ns1.dyndns.org.
dyndns.org.             86400   IN      NS      ns2.dyndns.org.
dyndns.org.             86400   IN      NS      ns3.dyndns.org.
dyndns.org.             86400   IN      NS      ns4.dyndns.org.
dyndns.org.             86400   IN      NS      ns5.dyndns.org.
;; Received 353 bytes from 2001:500:40::1#53(a2.org.afilias-nst.info) in 117 ms

foxwebhosting2.dyndns.org. 60   IN      A       74.105.56.53
dyndns.org.             86400   IN      NS      ns2.dyndns.org.
dyndns.org.             86400   IN      NS      ns3.dyndns.org.
dyndns.org.             86400   IN      NS      ns1.dyndns.org.
dyndns.org.             86400   IN      NS      ns5.dyndns.org.
dyndns.org.             86400   IN      NS      ns4.dyndns.org.
;; Received 369 bytes from 2600:2004::75#53(ns4.dyndns.org) in 274 ms
```
So, dig asked k.root-servers.net who is in charge of the .org top level domain. It gave us a big list out of which dig picked a2.org.afilias-nst.info to ask. a2.org.afilias-nst.info gave us a list of DynDNS' servers. Dig asked ns4.dyndns.org for the IPv4 address (the a record) of foxwebhosting2.dyndns.org and got the answer 74.105.56.53. Ok, good, everything is working as it should so far. Since we know from the first dig command that I can ask foxwebhosting2.dyndns.org (or foxwebhosting.dyndns.org) for computerfoxdesign.net IPv4 address, let's try it with dig.
(we'll ask 74.105.56.53 (which is the IPv4 address of foxwebhosting2.dyndns.org))
```
dig a computerfoxdesign.net @74.105.56.53
........
about 20 seconds pass
........
; <<>> DiG 9.7.1-P2 <<>> a computerfoxdesign.net @74.105.56.53
;; global options: +cmd
;; connection timed out; no servers could be reached

```
Hmmm, it appears we aren't able to connect to the foxwebhosting2.dyndns.org DNS server. Maybe the DNS server has port 53 (the DNS service port) firewalled/blocked/behind NAT? Maybe the DNS servers IP address has changed but the DNS for it hasn't?

So, what are my suggestions if you didn't get that whole long section of how I would look for the problem? Make sure your port 53 is forwarded. Make sure the BIND server program is running. Make sure that foxwebhosting2.dyndns.org points to the right address.

PS:If my post sounds grumpy, I'm not. :) I'm just trying to use this opportunity to show you how you can use the 'dig' command in a very hands on way, and to give you an idea of how the DNS system works.

---

### Post by SoftwareExplorer on 2011-01-25
Oh, I kind of forgot to tell you how the DNS fits in the picture:Even if we had Apache working the way we want, no web browsers would be able to connect to your computerfoxdesign.net site (because the DNS lookup would fail), and therefore all the browsers getting to your website would be saying in the request that they were coming for the other site, so it's pretty hard to test if apache is doing what we want until we get the DNS ironed out.

---

### Post by computerfox on 2011-01-25
i have great news and bad news.

the great news is that computerfoxdesign.net did work, but i have to make sure it's forwarding to the right directory.

the bad news is that what you gave me in the first post was a lot of information and did help a little, but i can see i have A LOT to learn for networking.

ps-it didn't sound grumpy at all, but even if it didn't i couldn't blame you.

---

### Post by computerfox on 2011-01-25
along with it not going to the right root, it doesn't work with [www.computerfoxdesign.net](www.computerfoxdesign.net) for some reason :(

---

### Post by SoftwareExplorer on 2011-01-25
I'm not sure, but maybe you need to make it so the roots for the various sites are in their own folders and not one inside the other?

---

### Post by computerfox on 2011-01-25
i'll try that.  give me one sec

---

### Post by SoftwareExplorer on 2011-01-25
I just looked at your screenshot again. I noticed that on the more specific virtual server, you have both the address to listen to and the servername to listen to set to the DNS name. I'm pretty sure that you should leave the address at any, but set the server name for each virtual host.
I think being able to specify the address is for if your server has multiple IP addresses (multiple connections, or just using more than one address for a connection), and you want to make each site listen to a specific IP (because then you could make one DNS name point at one IP, and the other DNS name point at the other IP).

---

### Post by computerfox on 2011-01-25
[IMG]http://computerfoxdesign.com/Pictures/temp1.png[/IMG]is this what you meant?

---

### Post by SoftwareExplorer on 2011-01-25
I get an error when I try to load the screenshot link in your last post.

I also just tried connecting to 74.105.56.53 port 53 and it rejected the connection. So I'm not sure if you forwarded your DNS server ports yet? You need to forward both port 53 UDP and port 53 TCP. Some programs use one protocol (like UDP) and others use another (like TCP).

Ok, now I can see the picture.

---

### Post by computerfox on 2011-01-25
yes, both ports are being forwarded.  it should be working, but [www.x.net](www.x.net) does not for some reason.

---

### Post by SoftwareExplorer on 2011-01-25
Any reason that the second entry has foxwebhosting.dyndns.org as the address?
Are you sure the DNS server is running? I keep getting "Destination Unreachable (Port Unreachable)" messages with UDP, and the connection gets reset (rejected, basically) if I use TCP.

What happens if you do ```
telnet 127.0.0.1 53
```

Do you get a message like 
```
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused

```
or more like 
```
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
----------------LONG PAUSE-------------------
Connection closed by foreign host.

```

If it's more like the first one, your DNS server isn't responding to requests.
I might also point out that [www.computerfoxdesign.net](www.computerfoxdesign.net) is different from computerfoxdesign.net. If you own the domain computerfoxdesign.net you own both of them, but they are different DNS names and could point to different IP addresses if you want. (Just like foxwebhosting.dyndns.org is different from dyndns.org, one points to your site, one points to the dyndns company's site. There's nothing special about the subdomain 'www'. It's just that a lot of sites point it to their main site.).

---

### Post by computerfox on 2011-01-25
changing that to "*" (any) enabled it to go to the correct directory.

i'm still having trouble with www

and give me a sec to take a look at the telnet

---

### Post by computerfox on 2011-01-25
yes, i checked the telnet and it is giving me the first messages.  does that mean that something isn't being forwarded?

---

### Post by SoftwareExplorer on 2011-01-25
> **computerfox said:**
> yes, i checked the telnet and it is giving me the first messages.  does that mean that something isn't being forwarded?

Ok, if you are running it on the DNS server (which I'm assuming your doing all you tests from) it means that you don't have your DNS server softare going.
127.0.0.1 is the IPv4 address that ALWAYS points to the current computer. (IPv6 eqivalent: "::1").
So you could have the forwarding for port 53 all right, but I think you will find it will go much better for you when have your DNS server going to take the requests when they get to the computer ;)

Your two sites in apache seem to be working properly now:I get two different pages when I go to foxwebhosting.dyndns.org and computerfoxdesign.net. 
(I got my browser to do this by changing my /etc/hosts file to make copmuterfoxdesign.net to your IP address. When your computer is looking up a DNS name, if /etc/hosts and the DNS network disagree, /etc/hosts wins. )

---

### Post by SoftwareExplorer on 2011-01-25
> **computerfox said:**
> 
i'm still having trouble with www

> **SoftwareExplorer said:**
> I might also point out that [www.computerfoxdesign.net](www.computerfoxdesign.net) is different from computerfoxdesign.net. If you own the domain computerfoxdesign.net you own both of them, but they are different DNS names and could point to different IP addresses if you want. (Just like foxwebhosting.dyndns.org is different from dyndns.org, one points to your site, one points to the dyndns company's site. There's nothing special about the subdomain 'www'. It's just that a lot of sites point it to their main site.).
I edited my comment to deal with the www question, right before you asked the question. (I wondered if you knew the difference because you referred to computerfoxdesign.net and [www.computerfoxdesign.net](www.computerfoxdesign.net) almost interchangeably in posts before the one I edited).

Try running ```
ps aux | grep -P "[n]amed"
```
IF you don't get any response like "bind      2247  0.0  0.4 228672 16372 ?        Ssl  Jan19   0:02 /usr/sbin/named -u bind" then your DNS server is not running. Try starting it with ```
sudo /etc/init.d/bind9 start
``` and see what happens. If it starts, you should get a response like  " * Starting domain name service... bind9                                 [ OK ]".

---

### Post by computerfox on 2011-01-25
adminabel@foxwebhosting:/etc/apache2/sites-available$ ps aux | grep -P "[n]amed"bind       859  0.0  0.7  61400 11120 ?        Ssl  16:56   0:00 /usr/sbin/name -u bind
adminabel@foxwebhosting:/etc/apache2/sites-available$ sudo /etc/init.d/bind9 start
 * Starting domain name service... bind9
   ...done.



how would i go about fixing that DNS problem?  would that be on the router or within the server?

---

### Post by SoftwareExplorer on 2011-01-25
Ok, I just checked again with the dig tool, and I got through to your DNS server.
```
dig a computerfoxdesign.net @74.105.56.53

; <<>> DiG 9.7.1-P2 <<>> a computerfoxdesign.net @74.105.56.53
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: REFUSED, id: 35724
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;computerfoxdesign.net.         IN      A  [COLOR="Red"]<IFitWORKEDther'dBEanADDRESShere>[/COLOR]

;; Query time: 172 msec
;; SERVER: 74.105.56.53#53(74.105.56.53)
;; WHEN: Tue Jan 25 23:15:21 2011
;; MSG SIZE  rcvd: 39


```

So, now your server is running. We just need to add DNS records to it and have it serve them. Are there any sections on DNS records in your administration interface? 
I would set up an 'a' record for computerfoxdesign.net. I would then make a 'cname' (stands for **C**anonical **N**ame. Points one DNS name to anther DNS name, instead of an address) record for [www.computerfoxdesign.net](www.computerfoxdesign.net) that points to "computerfoxdesign.net".


Edit:
> how would i go about fixing that DNS problem? would that be on the router or within the server?
Ok, so now your DNS server is going. The only problem left is to tell it to serve something.

---

### Post by computerfox on 2011-01-25
[www.x.net](www.x.net) comes up, but now the other one doe not.  lol :facepalm:

---

### Post by computerfox on 2011-01-25
i think i got it actually.  can you test from me from all the way there?

---

### Post by SoftwareExplorer on 2011-01-25
> **computerfox said:**
> [www.x.net](www.x.net) comes up, but now the other one doe not.  lol :facepalm:

If I look up foxwebhosting.dyndns.org it seems to go to the right place
```
dig a foxwebhosting.dyndns.org @2600:2002::75

; <<>> DiG 9.7.1-P2 <<>> a foxwebhosting.dyndns.org @2600:2002::75
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 25560
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 5, ADDITIONAL: 10
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;foxwebhosting.dyndns.org.	IN	A

;; ANSWER SECTION:
foxwebhosting.dyndns.org. 60	IN	A	74.105.56.53

;; AUTHORITY SECTION:
dyndns.org.		86400	IN	NS	ns3.dyndns.org.
dyndns.org.		86400	IN	NS	ns4.dyndns.org.
dyndns.org.		86400	IN	NS	ns1.dyndns.org.
dyndns.org.		86400	IN	NS	ns5.dyndns.org.
dyndns.org.		86400	IN	NS	ns2.dyndns.org.

;; ADDITIONAL SECTION:
ns1.dyndns.org.		60	IN	A	204.13.248.75
ns1.dyndns.org.		60	IN	AAAA	2600:2001::75
ns2.dyndns.org.		86400	IN	A	204.13.249.75
ns2.dyndns.org.		86400	IN	AAAA	2600:2002::75
ns3.dyndns.org.		86400	IN	A	208.78.69.75
ns3.dyndns.org.		86400	IN	AAAA	2600:2003::75
ns4.dyndns.org.		86400	IN	A	91.198.22.75
ns4.dyndns.org.		86400	IN	AAAA	2600:2004::75
ns5.dyndns.org.		86400	IN	A	203.62.195.75
ns5.dyndns.org.		86400	IN	AAAA	2600:2005::75

;; Query time: 184 msec
;; SERVER: 2600:2002::75#53(2600:2002::75)
;; WHEN: Tue Jan 25 23:43:14 2011
;; MSG SIZE  rcvd: 368


```

If I look up [www.computerfoxdesign.net](www.computerfoxdesign.net), it seems to work:
```
dig a www.computerfoxdesign.net @74.105.56.53

; <<>> DiG 9.7.1-P2 <<>> a www.computerfoxdesign.net @74.105.56.53
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10683
;; flags: qr aa rd; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;www.computerfoxdesign.net.	IN	A

;; ANSWER SECTION:
www.computerfoxdesign.net. 38400 IN	A	74.105.56.53

;; AUTHORITY SECTION:
computerfoxdesign.net.	38400	IN	NS	foxwebhosting.dyndns.org.

;; Query time: 173 msec
;; SERVER: 74.105.56.53#53(74.105.56.53)
;; WHEN: Tue Jan 25 23:45:32 2011
;; MSG SIZE  rcvd: 97


```

So, it seems to be working like it should from here.

---

### Post by computerfox on 2011-01-25
good grief!  i've been working one this for at least 3 weeks, but thank you so much.  do you think i should be okay with the rest or should i look at some more references?

---

### Post by SoftwareExplorer on 2011-01-25
I would recommend making another 'a' record for "computerfoxdesign.net" that points to the right address. Otherwise, if people type "computerfoxdesign.net" in their browser (forgetting the "www." part), they won't get to your site.

---

### Post by computerfox on 2011-01-25
i believe i did that.  the only time it doesn't work is if it's [http://computerfoxdesign.net](http://computerfoxdesign.net), but if you type in simply computerfoxdesign.net, it'll come up.  is the latter what you mean?

---

### Post by SoftwareExplorer on 2011-01-26
> **computerfox said:**
> good grief!  i've been working one this for at least 3 weeks, but thank you so much.  do you think i should be okay with the rest or should i look at some more references?
Well, if your writing web pages, you might consider writing them in xhtml. There's a pretty good site about web development, their xhtml 'course' is at [[COLOR="DeepSkyBlue"]http://w3schools.com/xhtml/default.asp[/COLOR]]("http://w3schools.com/xhtml/default.asp"). The whole site is a nice web development reference. I would say that the best way to learn is by doing. So, just try it, and if you get stuck search Google and then ask people for help.
> **computerfox said:**
> i believe i did that.  the only time it doesn't work is if it's [http://computerfoxdesign.net](http://computerfoxdesign.net), but if you type in simply computerfoxdesign.net, it'll come up.  is the latter what you mean?
Normally, your browser will add the "http://" part, so the two would be the same. however, maybe your browser is trying computerfoxdesign.net, and not being able to connect, so then it tries it with 'www.' added? My browser sometimes adds the 'www' if it can't connect. What happens if you do ```
dig a computerfoxdesign.net @127.0.0.1
```?

The reason I don't think you did it is that I asked your DNS server directly,  and I didn't get an address for computerfoxdesign.net.

Edit:Is your DNS server still running? I seem to be having trouble connecting directly to it.

---

### Post by computerfox on 2011-01-26
yeah, i agree.  xhtml is a nice language.  i usually write in that instead so i don't know why i wrote it in html, but it'll take me about 10 hours to move everything to xhtml.

---

### Post by SoftwareExplorer on 2011-01-28
I just rechecked the DNS today, and it seems like your DNS server is working and you have a DNS record for computerfoxdesign.net, so I would say everything is working. (But you probably already knew that). 
[[COLOR="DeepSkyBlue"]http://validator.w3.org/[/COLOR]]("http://validator.w3.org/") can check xhtml too see if it is correct and can try to suggest what code you should use instead, which might be helpful when changing pages from html to xhtml.

---

