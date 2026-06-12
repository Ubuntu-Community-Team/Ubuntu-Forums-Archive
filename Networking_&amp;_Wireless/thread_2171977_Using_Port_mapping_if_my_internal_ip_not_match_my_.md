---
title: "Using Port mapping if my internal ip not match my public ip"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by Raafat1991 on 2013-09-02
Hi guys...i'm wondering if my internal ip (which will be under my router's WAN settings) not match my public ip 
Can i use Port mapping ?



thank you *_________*

---

### Post by bkline on 2013-09-02
Sure.  The details on how you get to your router's administration menus will vary depending on which router you have, but basically you tell the router: For traffic coming in on port X (for example, port 80 if you're trying to handle web/HTTP requests), pass the packets to machine Y on that same port.  The external and internal ports don't have to be the same (and in fact they can't be, if you want to have more than one machine reachable for the same protocol).

Good luck!

---

### Post by Raafat1991 on 2013-09-02
Thank you for your reply but in fact you did't answer me,or Was my explanation for my problem incorrent ?

---

### Post by Iowan on 2013-09-02
Try rephrasing the question. Are you trying to access the public IP from inside the network?

---

### Post by Raafat1991 on 2013-09-02
I'm trying to access a local machine from outside my home's network but my internal ip not match my public ip

internal ip i mean ip which you can see under your router's WAN settings not your local ip on your local network (which you could figure out by issuing "ifconfig | grep inet").

---

### Post by 3rdalbum on 2013-09-03
The IP address displayed by your router's WAN page (or by whatismyip.com) is your external IP address. The IP address reported as yours in Network Manager is the internal IP address. Most routers should have a way of taking incoming traffic on one port and forwarding it to an internal IP address.

---

### Post by Raafat1991 on 2013-09-03
[COLOR=#ff0000][B]I have three IP addresss:
[/B][/COLOR]
first :192.168.1.13 i got it by issuing ifconifg 
second:100.68.23.220 (from my router's WAN status)
third:77.31.48.51 (i got it from this [http://whatismyipaddress.com/](http://whatismyipaddress.com/))

In this situation Can i use port Mapping ?

---

### Post by ian-weisser on 2013-09-03
> **Raafat1991 said:**
> In this situation Can i use port Mapping ?

Yes.
Set it up on your router, not on your Ubuntu system.

---

### Post by bkline on 2013-09-03
> **Raafat1991 said:**
> Thank you for your reply but in fact you did't answer me, ....

Sorry you thought I didn't answer your question.  "Sure" is a colloquial synonym for "Yes," which was the start of my reply to your question "Can I use port mapping?", which I followed with some more detailed information (or, as much detail as was available without knowing which router you're using) about how to go about it.

---

### Post by JKyleOKC on 2013-09-03
The other replies you've received are correct, but may not actually address your problem. It depends on what you want the port mapping to do!

Specifically, all that it can do is map one single port or a small group of ports -- not an entire IP address -- to either different ports at the same IP address, or to the same ports at a different IP address. Thus if you were running a web server behind your router, you could make it available to the outside world by mapping port 80 to your internal IP address where the server actually lives. However, you cannot map all ports to a different machine, if for no other reason than there are 65,535 of them and no router has a mapping table big enough to handle them all.

Most routers can handle a dozen or more mappings with ease, but once you get into the hundreds it's a different story. For the web server I mentioned as an example, you actually would have to map several other ports, depending on just what services your server was offering, but each mapping can handle only a few ports.

Hope this helps make things a bit more clear...

---

### Post by Raafat1991 on 2013-09-04
> **ian-weisser said:**
> Yes.
Set it up on your router, not on your Ubuntu system.

Please give me more explanations...

---

### Post by Raafat1991 on 2013-09-04
> **bkline said:**
> Sorry you thought I didn't answer your question.  "Sure" is a colloquial synonym for "Yes," which was the start of my reply to your question "Can I use port mapping?", which I followed with some more detailed information (or, as much detail as was available without knowing which router you're using) about how to go about it.

Please stay with us

---

### Post by ian-weisser on 2013-09-04
> **Raafat1991 said:**
> Please give me more explanations...

Several other participants in this thread have provided excellent explanations on what port mapping (port forwarding) is, and how to set it up on your router (which we know nothing about). There seems little point in repeating their fine work.

Please make your question more precise.
Are you asking how to change your router settings?
Are you asking what a port is?
Are you asking how the port forwaring process works on an Ubuntu system?
Are you asking how to forwat the port(s) of a specific service?
Are you asking how to set up a DMZ on your router?

---

### Post by Raafat1991 on 2013-09-04
> **JKyleOKC said:**
> The other replies you've received are correct, but may not actually address your problem. It depends on what you want the port mapping to do!

Specifically, all that it can do is map one single port or a small group of ports -- not an entire IP address -- to either different ports at the same IP address, or to the same ports at a different IP address. Thus if you were running a web server behind your router, you could make it available to the outside world by mapping port 80 to your internal IP address where the server actually lives. However, you cannot map all ports to a different machine, if for no other reason than there are 65,535 of them and no router has a mapping table big enough to handle them all.

Most routers can handle a dozen or more mappings with ease, but once you get into the hundreds it's a different story. For the web server I mentioned as an example, you actually would have to map several other ports, depending on just what services your server was offering, but each mapping can handle only a few ports.

Hope this helps make things a bit more clear...

Okay...i want to make my web server available from outside my home

my router's model number : huawi LTE CPE E5172,4G router

Also i have followed this guide [http://portforward.com/english/routers/port_forwarding/Huawei/HG533/defaultguide.htm](http://portforward.com/english/routers/port_forwarding/Huawei/HG533/defaultguide.htm) but there is no luck 


Any an idea ?


thank you everyone

---

### Post by ian-weisser on 2013-09-04
Did you encounter any problems following those instructions?
Did you follow ALL the instructions?

Did you set up a static IP for the server?
Does the server have that desired IP?

Is the server running?
Did you change any firewall settings on the server?
Can you reach the server from other machines on your local network behind the router?

Did you set up port forwarding on the router?

---

### Post by Raafat1991 on 2013-09-04
Did you encounter any problems following those instructions? No
Did you follow ALL the instructions? Yes

Did you set up a static IP for the server? Yes
Does the server have that desired IP? Yes

Is the server running? Yes
Did you change any firewall settings on the server? No
Can you reach the server from other machines on your local network behind the router? Yes

Did you set up port forwarding on the router? Yes


after i have followed this Test if your ports are open section i got that my port is CLOSED

---

### Post by scbingham on 2013-09-04
I was a bit confused by the second address (100.68.23.220) you listed earlier. Your actual external/public ip address is 77.31.48.51 This is the one issued to your router by your ISP. Is this a static address or dynamic (most are dynamic)?

If it is dynamic, you will need to set up a dynamic dns address which will always point to your router regardless of the ip address ie nameofyourchoice.dydns.com

There will be a field within your router to set this up. There are many free services available but check your router first as many manufacturers have deals with certain services. For example, my Dlink router allows me to set up a free dydns record. Dydns is no longer a free service.

I hope this helps.

---

### Post by ian-weisser on 2013-09-04
[QUOTE=Raafat1991;12778869
Can you reach the server from other machines on your local network behind the router? Yes

Did you set up port forwarding on the router? Yes

after i have followed this Test if your ports are open section i got that my port is CLOSED[/QUOTE]

Excellent. Now we know that the problem is your router or router settings.
Which ports did you forward, and what IP address did you forward them to? (Please list them all)

---

### Post by Raafat1991 on 2013-09-05
> **ian-weisser said:**
> Excellent. Now we know that the problem is your router or router settings.
Which ports did you forward, and what IP address did you forward them to? (Please list them all)

i have only one entry :

protocol :TCP/UDP
            remote host       : empty
remote port range : 80
        local host : 192.168.2.3
             local port : 80
          status : Enabled

---

### Post by ian-weisser on 2013-09-05
> **Raafat1991 said:**
> i have only one entry :

protocol :TCP/UDP
            remote host       : empty
remote port range : 80
        local host : [COLOR=#ff0000]192.168.2.3[/COLOR]
             local port : 80
          status : Enabled

At the beginning of the thread, you wrote that your server's IP address was [COLOR=#ff0000]192.168.1.13[/COLOR]
The router is directing port 80 packets to 192.168.2.3 instead.
Run ifconfig to double-check the server's current IP address.
Change the 'local host' field so it point to the server's current IP address.

---

### Post by JKyleOKC on 2013-09-05
@ian: Think that "remote host: empty" field might also be involved? It would depend on just how the router's internal code handles things, but seems possible that this could be the cause of the "connection refused" error he's showing in an earlier post...

---

### Post by Raafat1991 on 2013-09-05
> **ian-weisser said:**
> At the beginning of the thread, you wrote that your server's IP address was [COLOR=#ff0000]192.168.1.13[/COLOR]
The router is directing port 80 packets to 192.168.2.3 instead.
Run ifconfig to double-check the server's current IP address.
Change the 'local host' field so it point to the server's current IP address.

i said that at the beginning of my thread and i have chagned to the IP 192.168.2.3 because my router is using the network 192.168.2.0 and it has 192.168.2.1

---

### Post by Raafat1991 on 2013-09-07
Hi guys...

---

### Post by ian-weisser on 2013-09-07
Are you trying to say that you did set up port forwarding correctly on the router, and that the router really is forwarding port 80 to the correct server IP?

If so, then is your webserver running?
On the server, try **sudo netstat -tulpn** . Is your webserver listening on port 80?
Do you have a firewall on server turned on that is blocking inbound port 80 connections?

Do you have a firewall on the router that is blocking onbound port 80 connections?

---

### Post by Raafat1991 on 2013-09-08
> **ian-weisser said:**
> Are you trying to say that you did set up port forwarding correctly on the router, and that the router really is forwarding port 80 to the correct server IP?

If so, then is your webserver running?
On the server, try **sudo netstat -tulpn** . Is your webserver listening on port 80?
Do you have a firewall on server turned on that is blocking inbound port 80 connections?

Do you have a firewall on the router that is blocking onbound port 80 connections?

I think we are going to spend much time about this thread you ask me and i answer you and no luck and over again...

i think this question will end this thread...
 

Do you have three IP addresses and have you set up port forwarding successfully ?

Or 

Do you know any one has three IP addresses and has set up port forwarding successfully ?

Any one have read this post PLEASE answer me or if can any one provide a logical article (Even if you have three IP addresses one for you local machine and one on your router's WAN settings and one external you still can use port forwarding ).


thank you *____________*

---

### Post by JKyleOKC on 2013-09-08
> **Raafat1991 said:**
> Any one have read this post PLEASE answer me or if can any one provide a logical article (Even if you have three IP addresses one for you local machine and one on your router's WAN settings and one external you still can use port forwarding ).I have three such addresses; the WAN address is in the 99.x.x.x area, the router is on the 192.168.1.x/24 network, and my LAN is on 192.168.0.x/24. I have no problem at all forwarding ports 20 and 21 for FTP, but my WAN address is **static**, not **dynamic**. My router is a Motorola 3347, business class, from AT&T, and refers to port forwarding as a "pinhole" but handles it perfectly.

The problem you are having may very well be because you are on a dynamic IP, subject to change every 24 hours or possibly even sooner although many ISPs try to assign the same IP as long as possible. Try running one of the "what is my IP" web pages frequently to see if yours is changing. If it is, then something like dyndns or one of the other services will be necessary in order for anyone outside your LAN to get through!

---

### Post by Raafat1991 on 2013-09-08
> **JKyleOKC said:**
> I have three such addresses; the WAN address is in the 99.x.x.x area, the router is on the 192.168.1.x/24 network, and my LAN is on 192.168.0.x/24. I have no problem at all forwarding ports 20 and 21 for FTP


I think you are on a local network and your router on another and a default gateway between you ,it's intuitive that your router has an IP address and what you said above it's,that's not what i mean...

Please Does your router's WAN IP match your external IP ?

if so tell me how did you know it ?

if can you post some screenshots for your router's WAN IP ?

thank you *____________*

---

### Post by Raafat1991 on 2013-09-08
> **JKyleOKC said:**
> I
The problem you are having may very well be because you are on a dynamic IP, subject to change every 24 hours or possibly even sooner although many ISPs try to assign the same IP as long as possible. Try running one of the "what is my IP" web pages frequently to see if yours is changing. If it is, then something like dyndns or one of the other services will be necessary in order for anyone outside your LAN to get through!

Thank you for you interaction with me...

I'm sure that my IP did't changed when i'm trying to reach it outside my home

i visited this site [http://whatismyipaddress.com/](http://whatismyipaddress.com/) and i figured out my IP and i have used it to reach my server but there is no luck and after that i went back to this site [http://whatismyipaddress.com/](http://whatismyipaddress.com/) to be sure that my IP did't chagned and it's so.

---

### Post by linuxonbute on 2013-09-08
Is ufw enabled on your server?
```

sudo ufw status

```

---

### Post by JKyleOKC on 2013-09-08
> **Raafat1991 said:**
> Please Does your router's WAN IP match your external IP ?

if so tell me how did you know it ?Yes, it does match. The router has a status page that lists the WAN IP as well as the LAN IP range, and my customers have no problem reaching my server using that same IP which proves that it's the external address.

A screenshot would be no help at all to you, since every make of router has different configuration pages. The 3347 has many more specialized possibilities than do most home routers; I could configure it to recognize five different external IPs (for which I currently pay, but do not use) and pass them directly to specific machines on my LAN, for example. That's why I bought it in the first place, but then I found that the single static IP that my ISP wraps around those five others suffices for all my needs!

I actually deal with quite a few other IP addesses here, since I have a few virtual machines that use the 10.x.x.x range and NAT to link to my LAN through the host machines.

It might help you to install the wireshark package and look at all the packets involved when you try to connect from an external system; running a scan from GRC is one way to get packets sent to you from outside your LAN so you can see what is happening to them.

---

### Post by Raafat1991 on 2013-09-08
> **JKyleOKC said:**
> Yes, it does match


So that's not my case...my router's WAN IP does't match my external IP. **they are different**.


So we go back again to my question that i have mentioned before.

---

### Post by Raafat1991 on 2013-09-08
> **linuxonbute said:**
> Is ufw enabled on your server?
```

sudo ufw status

```

inactive.

---

### Post by ian-weisser on 2013-09-10
> **Raafat1991 said:**
> first :192.168.1.13 i got it by issuing ifconifg 
second:100.68.23.220 (from my router's WAN status)
third:77.31.48.51 (i got it from this [http://whatismyipaddress.com/](http://whatismyipaddress.com/))

Aha. Found it. So simple!
Seems like you have an ISP or upstream issue.

```
$ whois 77.31.48.51
[...]
inetnum:        77.31.0.0 - 77.31.255.255
netname:        SAUDINET_DSL_POOL
descr:          DSL HOME Subscribers

```


```
$ whois 100.68.23.220
[...]
NetRange:       100.64.0.0 - 100.127.255.255
[...]
NetType:        IANA Special Use
Comment:        This block is used as Shared Address Space. Traffic from these addresses does not come from IANA. IANA has simply reserved these numbers in its database and does not use or operate them. We are not the source of activity you may see on logs or in e-mail records. Please refer to http://www.iana.org/abuse/
Comment:        
Comment:        Shared Address Space can only be used in Service Provider networks or on routing equipment that is able to do address translation across router interfaces when addresses are identical on two different interfaces.
```

You have more than one router between your LAN and the internet. That upstream router may be local to you (like near the DSL modem), or it may be at Saudinet. Based on the IP address, the latter seems more likely to me.
For Port Forwarding to work, it must be set up on *all* the routers.

If Saudinet cannot rent you a useful IP address, I suppose you can start looking at VPNs, offsite hosting, and other workarounds to the ISP.

---

### Post by Raafat1991 on 2013-09-12
> **ian-weisser said:**
> 
I suppose you can start looking at VPNs, offsite hosting, and other workarounds to the ISP.

Please tell me more about your suggestion above

---

### Post by Raafat1991 on 2013-09-15
So simply i can't use port forwarding with this situation right ?

---

### Post by ian-weisser on 2013-09-15
> **Raafat1991 said:**
> So simply i can't use port forwarding with this situation right ?

Correct.
If you do not control the upstream router, then you cannot use port forwarding in the situation you described.

---

### Post by Raafat1991 on 2013-09-16
Thank you.

---

