---
title: "Ubuntu/VirtualBox networking issues"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by MarkPlatt on 2010-10-31
Hi there,
   
  A bit of a newbie so forgive any ignorance shown here. I do need some help.
   
  I’ve installed Ubuntu 10.04.1 into Oracle Virtual Box 3.2.10 running on XP (intel core 2 with 4 gig). The PC is running on a home network with another XP machine. Both connect to the internet via a D-Link G604T router.(Direct Wired)

   
  All is working well expect certain aspects of the network. For instance the Midori browser supplied with Ubuntu works a treat but Firefox is either diabolically slow or can’t find any address I enter. Both have similar settings in that both are directed to automatically detect the proxy server.
   
  Further I can use curl to download an http page (ie curl [http://curl.haxx.se]("http://curl.haxx.se/") will correctly download the page) but trying to install ruby using rvm mostly gives me an error (7) – cannot connect to host. I say mostly because I have managed to get 1.8.7 and 1.9.1 installed after trying around 4786 times (slight exaggeration[FONT=Wingdings]J[/FONT]).
   
  It’s mostly the intermittency that is confusing me. I can’t seem to get a consistent connection that applies to all applications. I’ve had the most success by using the Bridged adaptor settings.
   
  Any help would indebt me forever.

---

### Post by eric_1982 on 2010-11-01
what happens when you try to ping some of the URLs? Are you getting dropped packets? Have you tried do a traceroute to see the path it takes?

Are you using your ISP DNS settings or have you manually configured a DNS server like Google or opendns?

---

### Post by MarkPlatt on 2010-11-01
> **eric_1982 said:**
> what happens when you try to ping some of the URLs? Are you getting dropped packets? Have you tried do a traceroute to see the path it takes?

Are you using your ISP DNS settings or have you manually configured a DNS server like Google or opendns?


Hi, thanks for the reply.

Yes I can ping [www.google.com](www.google.com) and get 100% success.

No I haven't modified any DNS settings. They are defaults.

Traceroute, again with google as my target gives me, what I would have thought, was an acceptable response. (although I'm not that sure)

Hop Hostname IP Time 1 Time 2
1 mark-desktop.local 10.1.1.4 0.148ms 
1 mygateway1.ar7 10.1.1.1 1.678ms 
1 mygateway1.ar7 10.1.1.1 1.199ms 
2 mygateway1.ar7 10.1.1.1 1.060ms 
2 125-239-64-1.jetstream.xtra.co.nz 125.239.64.1 34.109ms 
3 no reply 
4 ae4-10.akbr5.global-gateway.net.nz 202.37.244.221 43.233ms
5 ae1-2.akbr4.global-gateway.net.nz 202.50.232.77 43.108ms 
6 ae1-10.tkbr9.global-gateway.net.nz 202.50.232.37 43.235ms 
7 so6-1-1.labr5.global-gateway.net.nz 122.56.127.62 176.396ms 
8 so0-0-1.lebr6.global-gateway.net.nz 202.50.232.98 177.938ms 
9 no reply * 
10 no reply *
11 no reply * 
12 no reply *
13 no reply *
14 no reply *
15 no reply *
16 no reply *
17 no reply *
18 no reply *
19 no reply * 
20 no reply * 
21 no reply * 
22 no reply * 
23 no reply * 
24 no reply * 
25 no reply * 
26 no reply * 
27 no reply *
28 no reply * 
29 no reply * 
30 no reply *
31 no reply *

---

