---
title: "Unable to connect to a small number of random websites:  Otherwise networking is fine"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by gimfred on 2010-12-29
Okay. I have a crazy problem.

I was having no problems (that I knew of) browsing the web since installing Ubuntu 10.10 a week or so ago. I was previously trialling Win7 as my customers will likely be using that in the future.

Then I wanted to go to internode.on.net. Got the following:
> Firefox can't establish a connection to the server at internode.on.net. or
> 
Oops! Google Chrome could not connect to internode.on.net

As it was just after Christmas I thought it must be down, for upgrades or maintenance etc. I later tried to go to Freebsd.org; same error. I've been having a small number of other websites give the same error. I thought nothing of this until I tried it on my wife's macpro. I could log onto all the websites I wanted to and none gave any indication of having been down. Both boxes are on the same adsl connection.

I still can't access internode or freebsd on 10.10 yet have been able to access every website on OSX. Now, I was only looking at them for info but am worried I won't be able to access something important. (so far everything I 'need' is working)

ping just drops out.

edit: weirdest thing! I just retried and now can not emulate the problem for internode. freebsd still won't show. that is less than five minutes between problems and resolution! Thanks people! I hadn't even posted! But I still would like to have an idea of what is going on. Here is the ping error for freebsd: 
> ping -c 4 freebsd.org
PING freebsd.org (32.1.4.248) 56(84) bytes of data.

--- freebsd.org ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3005ms

 what else can I try to figure out what is going on?

---

### Post by supershin on 2010-12-29
you can run a traceroute. It shows where the requests are being made at each point between your pc and the site. It should be under network tools in the tab next to ping. The command line is most likely tracert site.com

---

### Post by gimfred on 2010-12-30
As I feared, it has got more serious: I can't install extensions!

```
:~$ traceroute https://addons.mozilla.org
https://addons.mozilla.org: Name or service not known
Cannot handle "host" cmdline arg `https://addons.mozilla.org' on position 1 (argc 1)
:~$ traceroute http://addons.mozilla.org
http://addons.mozilla.org: Name or service not known
Cannot handle "host" cmdline arg `http://addons.mozilla.org' on position 1 (argc 1)

```
```
:~$ traceroute addons.mozilla.org
traceroute to addons.mozilla.org (63.245.209.91), 30 hops max, 60 byte packets
 1  mygateway1.ar7 (10.1.1.1)  0.743 ms  0.991 ms  1.232 ms
 2  * * *
 3  bri-sot-wic-csw2-gi-1-3.tpgi.com.au (202.7.173.137)  49.130 ms  52.708 ms  56.143 ms
 4  bri-sot-wic-crt1-gi-2-0-0.tpgi.com.au (203.29.135.1)  59.429 ms  62.250 ms  65.176 ms
 5  bri-nxg-alf-crt1-POS-8-0.tpgi.com.au (202.7.171.253)  69.441 ms  72.532 ms  75.707 ms
 6  syd-sot-ken-crt1-TG-7-0-0.tpgi.com.au (202.7.171.125)  96.004 ms  92.480 ms  96.092 ms
 7  xe-7-0-0.edge1.SanJose3.Level3.net (4.53.208.13)  280.010 ms  240.742 ms  240.614 ms
 8  ae-2-79.edge8.SanJose1.Level3.net (4.68.18.84)  240.742 ms ae-4-99.edge8.SanJose1.Level3.net (4.68.18.212)  240.844 ms  240.898 ms
 9  CWIE-LLC.edge8.SanJose1.Level3.net (4.53.30.34)  297.297 ms  293.247 ms  290.207 ms
10  te-8-2.core2.sjc.mozilla.net (63.245.208.98)  248.437 ms  244.743 ms  245.085 ms
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```
```
 releases.mozilla.org
traceroute to releases.mozilla.org (32.1.6.176), 30 hops max, 60 byte packets
 1  mygateway1.ar7 (10.1.1.1)  0.559 ms  0.805 ms  1.052 ms
 2  * * *
 3  bri-sot-wic-csw1-gi-1-3.tpgi.com.au (202.7.173.125)  49.452 ms  52.833 ms  55.752 ms
 4  bri-sot-wic-crt1-gi-2-1-0.tpgi.com.au (202.7.171.217)  59.260 ms  62.371 ms  65.540 ms
 5  bri-nxg-alf-crt2-POS-7-0.tpgi.com.au (202.7.171.245)  69.290 ms  72.650 ms  75.819 ms
 6  syd-sot-ken-crt2-ge-0-0.tpgi.com.au (202.7.171.133)  90.951 ms  87.523 ms  91.157 ms
 7  Vlan516.icore1.SQN-SanJose.as6453.net (66.198.97.33)  289.159 ms * *
 8  if-5-1886.tcore2.LVW-LosAngeles.as6453.net (209.58.116.38)  251.363 ms  250.926 ms  251.008 ms
 9  if-2-2.tcore1.LVW-LosAngeles.as6453.net (66.110.59.1)  251.083 ms  251.181 ms  250.489 ms
10  192.205.35.129 (192.205.35.129)  248.606 ms  244.222 ms  244.850 ms
11  cr2.la2ca.ip.att.net (12.122.129.34)  310.922 ms  310.305 ms  310.410 ms
12  cr1.slkut.ip.att.net (12.122.30.29)  310.622 ms  310.761 ms  310.677 ms
13  cr2.dvmco.ip.att.net (12.122.30.26)  310.349 ms  310.253 ms  312.391 ms
14  cr1.cgcil.ip.att.net (12.122.31.86)  310.794 ms  309.750 ms  309.960 ms
15  cr2.wswdc.ip.att.net (12.122.18.22)  310.911 ms  309.617 ms  309.236 ms
16  12.122.134.237 (12.122.134.237)  309.610 ms  309.538 ms  308.942 ms
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *

```
```
:~$ ping -c 4 releases.mozilla.org
PING releases.mozilla.org (32.1.6.176) 56(84) bytes of data.

--- releases.mozilla.org ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3005ms

```

---

### Post by PatchesTheCaveman on 2010-12-30
You won't be able to complete a traceroute to a lot of sites because of the way their networks or set up.  Google is an exception.  You might be missing hops but you can always make it to the final server in Google's network.

Pinging releases.mozilla.org is a bad test too because that host points a random IP address for any one of hundreds of servers in their mirror network.

If you can get the full path to the addon you're downloading, try changing releases.mozilla.org to ftp.mozilla.org.  For example, change [http://releases.mozilla.org/pub/mozilla.org/addons/5/phoenity-1.4.1-fx.jar](http://releases.mozilla.org/pub/mozilla.org/addons/5/phoenity-1.4.1-fx.jar) to [http://ftp.mozilla.org/pub/mozilla.org/addons/5/phoenity-1.4.1-fx.jar](http://ftp.mozilla.org/pub/mozilla.org/addons/5/phoenity-1.4.1-fx.jar)

The problems you're experiencing sound like they're your ISP's fault, not anything in your setup.  That being said there's one command you can run that might reveal something funky:
```
route
```

There might be something weird in your routing table that's sending traffic somewhere it shouldn't.

---

### Post by gimfred on 2010-12-31
Well thanks bloke!

Ah... route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         mygateway1.ar7  0.0.0.0         UG    0      0        0 eth0

```
Should the first interface be 10.1.1.1? That is, my 'router', or should it be my machine .5?

---

### Post by cyb3r_sn4k3 on 2010-12-31
Tried pinging the site and using the ip as the address?

---

### Post by gimfred on 2010-12-31
ping freebsd.org, get 69.147.83.40

using the ip gets me the same problem:

"Firefox can't establish a connection to the server at www.freebsd.org."

It is obvious DNS is working, so I guess it is likely to be my ISPs (tpg.com.au) trying to be too fancy and stuffing it up. Does everyone agree?

I have noticed a trend of not being able to access sites regarding the alternative software worlds howtos, hints tips and features. Of course I don't do much in the more mainstream web nor have much interests out side tech sites, for now. So I don't have a good representation.

---

### Post by supershin on 2010-12-31
> "Firefox can't establish a connection to the server at www.freebsd.org."

Ping should've been run from terminal. Make sure firefox isn't set to work offline, you'll find it under File.

---

### Post by gimfred on 2011-01-01
ping was done from a terminal; that message is what I get when I use the ip address, which is the same as using the url.

Firefox is not off-line; I can access most sites, it is just a few don't work. 

It is a weird problem

---

### Post by PatchesTheCaveman on 2011-01-01
Your routing table is correct.  This line:
```
10.1.1.0        *               255.255.255.0   U     1      0        0 eth0
```
just means that all traffic on your local network is sent directly and not through your gateway (router).

Your ISP's name servers could be reporting the wrong IP address for a few hosts.  You can try switching DNS servers and see if that will help.  

To do so, right-click on the network icon in your top panel, click *Edit Connections...*.  Find your connection in the box that appears, click on it, and click *Edit*.  Switch to the *IPv4 Settings* tab.  If your *Method* is set to *Automatic (DHCP)*, change it to *Automatic (DHCP) addresses only*.  Under DNS servers, enter the following:
```
8.8.8.8,8.8.4.4
```.  Click *Apply* and *Close*.

Give the sites that weren't working a try again.  You might need to reboot to clear any caches and let the new servers take effect.

The DNS servers I provided are the free public ones provided by Google.  You can also use OpenDNS or any other DNS provider.  I prefer Google to OpenDNS because OpenDNS shows ad-sponsored search pages when you try to visit a domain that doesn't exist while Google properly returns a *NXDOMAIN* response.  For more information on Google's public DNS service, visit [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

---

### Post by gimfred on 2011-01-04
@PatchesTheCaveman:
Thanks, changing the DNS servers worked. Still, it is a bit weird that the problem only showed up under Ubuntu. Marking Solved.

In case anyone is confused the solution follows:

1. Change DNS server(s) in network.*
2. reboot**

* In my case I used Google's public DNS as provided by PatchesTheCaveman

** I suspect this is not strictly needed, but I could have stopped/restarted network connections; rebooting is so Microsoft. I should really learn to manage my box better.

---

