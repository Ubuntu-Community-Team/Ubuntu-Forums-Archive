---
title: "Internet Working; Ping Not"
date: 2012-02-06
forum: Networking &amp; Wireless
---

### Post by bailewen on 2012-02-06
Been googling this issue for about an hour or so with no luck . . .

Here's a variation for you...I am online just fine but I can't even ping my own router (192.168.1.1)

I can ping 127.0.0.1 and I can ping my own address behind the router but nothign else, not even the other computer on my home network (Windows XP). The XP box, OTOH, can ping me just fine which makes me think I somehow disabled icmp. :confused:

ip rou gives me the following:> 
default via 192.168.1.1 dev wlan0  proto static 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
192.168.1.0/24 dev wlan0  proto kernel  scope link  src 192.168.1.101  metric 2 


Maybe UFW is blocking it somehow? Like I said, I can access the internet just fine. I'm just playing around with my home network and trying to learn how to up security since my XP box is currently being hacked. (found the hacker through netstat but the linux box appears safe. . . for now) 

The weirdest thing of all is that if I put 192.168.1.1 into the browser address bar I still get the logon page but ping gets nothing. 

Any idea what's going on?

---

### Post by jonobr on 2012-02-06
Either your router is set to not respond-to ICMP requests which is highly likely ,
or you have a rule in UFW.

I think the first one is the most likely one.

Best way to test is

```
sudo tcpdump - i any icmp
```
then when you do a ping, the above trace will show you the icmp message go out (icmp request) and then one in return,
icmp response.
If you see the first but not the second , the router is not responding.
If you see the first and the second, but ping failing it may be dropped after it is received.
If you see neither, its blocked from going out

---

### Post by bailewen on 2012-02-06
> I think the first one is the most likely one.
Really? I thoguth I had ruled out the router since the other computer on my network can ping just fine. 

Just the same, I'm happy to try whatever you suggest so . . .

> tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: syntax error

That's suggestive. :) Not sure exactly what that means except that IPv4 is an internet protocol and when I set rules in UFW it often tells me either an IPv4 or an IPv6 rule has been added.

edit:
Thanks for the clue. I just discovered that if I disable the router's firewal, suddenly I can ping it. Also I found that if I uncheck "prevent any packets coming from the LAN from passing through the router" (<--roughly translated from the Chinese)


That still doesn't explain why the other computer on the network could ping me regardless of these settings. . . . :(

---

### Post by jonobr on 2012-02-07
Hey There


Just reading your update now.

I didnt notice that you said you could ping from another machine to that interface 

The only thing I can think of is there is a trusted list of clients or its treating one machine different to another.

Kind of odd it responds.

The whole idea of this is to stop machines that ping ranges of IP addresses, find a target and then attack it.
Anyway, IM not sure where we stand on this if its resolved or not??

One of the weird ones:-)

---

