---
title: "Ip failover"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by bonesjones256 on 2012-02-09
Got a weird one. 

Here's my current setup. 

WANIP=>>>>\  Firewall\   Server
WANIP2=>>>/  Firewall/   Server

Basically our company is in an area where all we can get is cable modem and Uverse. The cable modem is fast 50 down 5 up. but goes down at least once a month (it's a constant fight with charter)

So I've got two static ips that point to the same stuff. one firewall with same ports open.
Outbound is fine my sonicwall knows if the WAN is out to send traffic out of WAN2. 

But incoming is the issue. I found a company that gives me a linux server for 20 bucks a month. What i am looking for is to redirect my dns to the ip of that linux server, have that linux server somehow monitor both of my WANS, normally i would want the server to forward all traffic to 80,25,5053 to the WAN1, however if wan one dies i want the server then send traffic to WAN2. 
And onces wan1 comes back send it back to wan1
That way if WAN one dies our website stays up, we can still get e-mail on our phones, and our monitoring system (port 5053) will still function. 

Everything i've read is for server failover, but i never have servers issues, but i have WAn issues constantly.

So in short I would change my dns records to point to the virtual server then from there send to either one of the servers, 
I realize there'd still be a single point of failure but a linux server failure rate is much less than that of my cable modem.

---

### Post by bonesjones256 on 2012-02-10
bump

---

### Post by jonobr on 2012-02-10
Hey

You may have better luck on the server forum,
I have seen solutions using balancing and failover, 
the people there may have more experience dealing with providers who will provide resolution to IP or IP 2 depending on conditions.

Mind you, a lot of the guys on the server forum keep an eye on the networking forum too

---

### Post by bab1 on 2012-02-10
> **jonobr said:**
> Hey

You may have better luck on the server forum,
I have seen solutions using balancing and failover, 
the people there may have more experience dealing with providers who will provide resolution to IP or IP 2 depending on conditions.

Mind you, a lot of the guys on the server forum keep an eye on the networking forum too

Psssst!  Don't get him started on that.  He already got pinched for double posting.  This problem has only tangential interest in the server section.  

It's a network problem for sure.  I believe fail over might be  handled via having two sub networks with contiguous range carved out of your main network.  I don't see reason why the hosts can't have multiple IP addresses (one in each range).  Apache (or whatever) may have to be configured for the multiple IP addresses pointing to it, but that should be easy enough.

By range I mean, for example, splitting in half a /24 range (i.e. 1192.168.1.0/25 and 192.168.1.128 /25)

---

### Post by jonobr on 2012-02-10
Yikes Bab1

Ill get back in my box :D

---

### Post by bab1 on 2012-02-10
> **jonobr said:**
> Yikes Bab1

Ill get back in my box :D

It turns out that the problem has 2 approaches one could take.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.networkingunlimited.com/white008.html") for ideas.

Multihoming a host and providing NAT to a network behind it is one idea.  It will provide Internet connectivity fail over for *your* network but not IP address agnostic service for others to connect to you. 

BGP is a little heavy duty for the end user but, *_when we need to support a common IP address range using both ISPs we do need to run BGP_*; as the reference above states.

Google is full of [**_[COLOR="Blue"]ideas[/COLOR]_**]("https://www.google.com/search?q=dual+wan+failsafe&btnG=Go!#sclient=psy-ab&hl=en&source=hp&q=multiple+ISP+without+BGP&pbx=1&oq=multiple+ISP+without+BGP&aq=f&aqi=&aql=&gs_sm=3&gs_upl=1140l9632l4l10096l24l21l0l3l3l0l339l4375l0.16.3.2l24l0&fp=1&biw=1169&bih=636&bav=on.2,or.r_gc.r_pw.,cf.osb&cad=b") on this subject.  It really depends what your needs are.

As you say @jonobr, server folk hang out here too.  ;-)

---

### Post by jonobr on 2012-02-10
I have been know to poke my nose into server to! :p

---

### Post by bonesjones256 on 2012-02-10
No offense but none of the above information helped. Seems no one can understand my situation, anyway if for any reason someone gets in the same situation the program called crossroads is the solution. So basicly here's my setup now and it works wonderful.


DNS name pointed at ip of linux server in the cloud through a large company that pretty much just ain't gonna go down. 

Then you have crossroads setup, you tell it what ports and what ip address it should send to, once a request is made it checks my hosts in order everytime first one that answers wins, which will be my cable modem unless it's down in which case the uverse line answers. All this happens in a split second and the setup is great. And it follows my Philosophy of using the KISS (Keep it simple stupid) method. 

Been in the linux world for many many years and my biggest problem is that most linux geeks (like myself) are TO SMART and they turn something like this into a rube goldberg machine. This is a very simple idea and works well. Yes there is a single point of failed the linux server in the cloud but it costs 20 bucks a month and its the ONLY thing running on it. and with these big companies an internet outage is extremely rare. 

Thanks for the few that offered to help, as far as the double post goes, what's the problem, posted my question here, never got a single reply, so i thought well maybe i should ask the server guys

---

