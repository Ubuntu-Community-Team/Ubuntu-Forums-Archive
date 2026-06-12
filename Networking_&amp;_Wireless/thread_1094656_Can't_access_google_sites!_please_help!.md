---
title: "Can't access google sites! please help!"
date: 2009-03-12
forum: Networking &amp; Wireless
---

### Post by gurukreff on 2009-03-12
Hello everybody.

I have this problem, i installed ubuntu intrepid in my girlfriend laptop's a while ago and everything worked fine, but recently she's been having this problem that she cant access google, gmail or any other google website.

What happens is that google sites load for a long time (10 min) and then firefox says that the website can't be reached. I don't have any kind of problem with other websites.

I'm behind a router here, and the two other pc's at the house are running perfectly fine (one desktop and another laptop). They reach google with no problem 

I checked the router and it isn't blocking any site, neither is firefox (in fact i tried other browsers with no success). I cleared the cookies and there is nothing unusual in /etc/hosts.deny.



Here's the output of a ping made to google.com:

```
PING google.com (209.85.171.100) 56(84) bytes of data.
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=1 ttl=242 time=197 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=2 ttl=242 time=211 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=3 ttl=242 time=227 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=4 ttl=242 time=212 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=5 ttl=242 time=443 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=6 ttl=242 time=217 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=7 ttl=242 time=196 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=8 ttl=242 time=197 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=9 ttl=242 time=370 ms
64 bytes from cg-in-f100.google.com (209.85.171.100): icmp_seq=10 ttl=242 time=230 ms

--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9025ms
rtt min/avg/max/mdev = 196.569/250.420/443.253/80.615 ms
```




And here's an output of the traceroute:

```
Salto	host		IP                             Tiempo 2
1	hermanal.local	192.168.0.180	                0.102ms	
1	192.168.0.1	192.168.0.1	                2.714ms	
1	192.168.0.1	192.168.0.1	                2.492ms	
2	no	reply	                                  *	
3	pc-129-250-104-200.cm.vtr.net 200.104.250.129	27.670ms	
4	200.27.16.1	200.27.16.1	                17.091ms	
5	san2-telmex-4-cl.san.seabone.net 195.22.221.69  14.894ms	
6	no	reply	*	
7	no	reply	*	
8	unassigned.bai.seabone.net	195.22.220.189	78.401ms	
9	no	reply	*	
10	no	reply	*	
11	no	reply	*	
12	no	reply	*	
13	no	reply	*	
14	no	reply	*	
15	no	reply	*	
16	no	reply	*	
17	no	reply	*	
18	no	reply	*	
19	no	reply	*	
20	no	reply	*	
21	no	reply	*	
22	no	reply	*	
23	no	reply	*	
24	no	reply	*	
25	no	reply	*	
26	no	reply	*	
27	no	reply	*	
28	no	reply	*	
29	no	reply	*	
30	no	reply	*	
31	no	reply	*	


```


Also i noticed that i can reach google.com in my browser if i use google's IP instead of the URL. I've done some searching on the internet and some guys say that maybe there's a problem with "hosts" files, here's the output of $cat /etc/hosts:


```

# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
```




That's it, hope that it's enough info, thanks for your help!

---

### Post by inobe on 2009-03-12
google gave me problems accessing it today' i believe the site was down...

in fact about an hour ago it was back up' but took a minute or so to load

give it a try now

---

### Post by gurukreff on 2009-03-12
I wish it was a google thing, but in fact this has been going on for three days now and it works on every other computer!

Thanks anyway :)

---

### Post by mcla0203 on 2009-03-12
I'm not sure what the solution of this means, but it appears this has occured for someone else before too.  You might want to take a look at this thread and see if you can make any sense of the solution.

[http://ubuntuforums.org/showthread.php?t=612225]("http://ubuntuforums.org/showthread.php?t=612225")

Good luck.

---

### Post by thesavager on 2009-03-12
Hi gurukreff,

When you can acces google using IP address , and not with domainname , then you have a dns problem.

try:

```
cat /etc/resolv.conf
```

U should see something like this :

search openna.com
nameserver 208.164.186.1
nameserver 208.164.186.2

If not, then try to reconfig your network-card.

cheers..

---

### Post by rfruth on 2009-03-12
lots of Google sites (gmail, news, docs etc.) were down for me earlier today (Thurs 12th) but ok now (a few hours later)

---

### Post by gurukreff on 2009-03-12
I don't have MoBlock installed, but maybe something else is blocking my access to google from here. Maybe a worm or virus changed some configs, is it possible?

If it is, someone could recommend me a good antivirus fo Ubuntu? (i thought i'd never live to see this day! :( )

---

### Post by gurukreff on 2009-03-12
> **thesavager said:**
> Hi gurukreff,

When you can acces google using IP address , and not with domainname , then you have a dns problem.

try:

```
cat /etc/resolv.conf
```

U should see something like this :

search openna.com
nameserver 208.164.186.1
nameserver 208.164.186.2

If not, then try to reconfig your network-card.

cheers..

Bingo!

i think you nailed it, this is the output of cat /etc/resolv.conf:

```
# Generated by NetworkManager
nameserver 192.168.0.1
```


Now may i ask you, what do i have to do? change the IP of the name server to my ISP's DNS server?

Thank you!


EDIT: Just realized that this it my Router's IP, do i have to do something there? consider that other laptop connected wirelessly doesn't have this problem

---

### Post by thesavager on 2009-03-12
You dont need an antivirus on linux , lol

But if you want to check the files you sent to your friends, i reccomend AVG for linux , it doesnt delete the infected files, this must be done by hand ,(Since it has no impact on the system), but does find them , and clamav doesnt. Clamav is shipt with xubuntu.

But really , who needs an antivirus on a unix-system :)

cheers ..

---

### Post by thesavager on 2009-03-12
Since it is your router IP , you dont have to change IP , your router should do the job for you (dns-resolving).
But you may add one more dns-server, take one from your ISP.

Also a possibillity , if you have a modem/router with embedded software.
Try unplug it from power for a minute , then back on again.

---

### Post by gurukreff on 2009-03-12
> **thesavager said:**
> Since it is your router IP , you dont have to change IP , your router should do the job for you (dns-resolving).
But you may add one more dns-server, take one from your ISP.

Also a possibillity , if you have a modem/router with embedded software.
Try unplug it from power for a minute , then back on again.

Savager, you did the trick!

I searched and realized that my ISP's DNS servers are crap, so i followed the suggestion of some guy that posted in a blog that a solution was to use a free DNS server such as [opendns.com]("http://www.opendns.com") and i used it in my router's configuration as my official DNS server and it worked, so everything's solved!

Thanks for your help, i'm so happy now! :D

---

### Post by thesavager on 2009-03-14
Hi gurukreff, i'm glad it worked out for you  :)

Nice link you added , didn't know that one :)  very handy thnx.

---

### Post by MiniZiper on 2009-05-02
> **gurukreff said:**
> Savager, you did the trick!

I searched and realized that my ISP's DNS servers are crap, so i followed the suggestion of some guy that posted in a blog that a solution was to use a free DNS server such as [opendns.com]("http://www.opendns.com") and i used it in my router's configuration as my official DNS server and it worked, so everything's solved!

Thanks for your help, i'm so happy now! :D

Well, what are the chances, I'm in Chile too, and I can't access Google servers either (youtube, gmail... etc).

But I CAN with windows. On the same laptop/router/modem/ISP... the OS is the only thing that makes the difference. You sure DNS is the problem? :S

Yahoo search is awful, and I'm tired of it.

---

### Post by MiniZiper on 2009-05-02
> **MiniZiper said:**
> Well, what are the chances, I'm in Chile too, and I can't access Google servers either (youtube, gmail... etc).

But I CAN with windows. On the same laptop/router/modem/ISP... the OS is the only thing that makes the difference. You sure DNS is the problem? :S

Yahoo search is awful, and I'm tired of it.

NVM, I switched to OpenDNS... it works now. I just don't get why Linux couldn't access google when Windows could with the original DNSs from my ISP.


I wonder how OpenDNS gets the money for their servers...

---

