---
title: "preparing for world ipv6 day"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by phen on 2011-05-09
hey all,

turning ipv6 off is afaik the easiest way to stay online on the world day in one month (I think its June 8, 2011?), but what would be required to switch to ipv6 for that day? or at least check the dual-stack operation?

are there any test pages or something?

bye

---

### Post by lemming465 on 2011-05-09
On [world IPv6 test day]("http://isoc.org/wp/worldipv6day/"), organized by the Internet Society, many organizations are going to v6-enable their websites and advertise AAAA records in DNS for 24 hours on June 8th (UTC).  Depending on your timezone, it might start on June 7th or end on June 9th.   The web sites will be "dual-stacked", meaning they will advertise both A (32-bit IPv4) and AAAA (128-bit IPv6) addresses in DNS, and serve the same web content via both addresses and protocols.

For 99.7% of internet users, they will see no difference, being on IPv4-only or IPv4-mostly.  About 0.1% of internet users will be aggressively using IPv6, and may or may not notice.  The remaining 0.2% have broken dual-stack configurations, such as bad 6to4 tunnel configurations on Apple OS-X 10 prior to 10.6.5, and may have connection delays between 20 seconds and 4 minutes, or complete failures to connect to web sites.

Internet service providers and colocation hosting services and cloud providers and web site content providers will be watching to see how much IPv6 traffic they get, and what kinds of problems turn up.

To see how you are likely to fare on IPv6 test day when web sites dual-stack, or with future web sites which might be IPv6-only, my favorite test site is [test-ipv6]("http://www.test-ipv6.com/").  Its even quasi-official I suppose, since the internet society is linking to it. It will try various things using v4 and v6 transport, and let you know how you are likely to do.  If you go to the non-summary tabs such as "technical info" it will interpret what the results of each test mean for you.

If Linux users want to experiment with IPv6, you have several options:

a) best - your ISP offers native (or 6rd near-native) IPv6, your broadband modem and wifi router support both IPv4 and IPv6.  Your Linux, OS-X, or Windows-7 clients are configured by default for dual-stack operation, so your test results should be 10/10 for dual-stack and 10/10 for v6-only.

b) good - set up an account with a tunnel broker service such as tunnelbroker.net (hurricane electric), sixxs, or gogo6, configure your client for 6in4 tunneling following the site's directions, and have fun.  Your local gear needs to pass protocol 41 (IP in IP) traffic, or maybe protocol 47 (GRE).

c) mediocre - use 6to4 anycast tunneling.  This requires protocol-41 support and a public, non-RFC-1918, IP address.  Failure rates on IPv6 connections can be as high as 15% and latency will be bad.  My favorite 6to4 setup script is from [New Zealand ISP anyweb]("http://www.anyweb.co.nz/tutorial/Linux6to4Host")

d) terrible - use Teredo UDP tunneling.  This requires installing the "miredo" client (sudo aptitude install miredo), will have truly horrible latency, and may have the same high failure rates as 6to4.

Note that for dual-stack web sites most operating systems will prefer native connections to 6to4 or Teredo tunnels, so on world IPv6 day you would mostly be using IPv4 anyway.  To force IPv6, you can either tune /etc/gai.conf, which is complicated, or put raw IPv6 addresses into URL's in square brackets, e.g.
    [http://[2001:200:dff:fff1:216:3eff:feb1:44d7]](http://[2001:200:dff:fff1:216:3eff:feb1:44d7])
to visit [www.kame.net](www.kame.net) on IPv6.

---

### Post by Cybjit on 2011-05-26
[Test-ipv6.com]("http://test-ipv6.com") is great, but unfortunately there is no good info on what to do on Ubuntu if you are broken.
Most people seems to assume the best course of action is to disable IPv6, but that is the sledgehammer approach.
A more refined way is to deprefer IPv6 by entering this in /etc/gai.conf
```

label ::1/128       0
label ::ffff:0:0/96 1
label ::/0          2
label 2002::/16     3
label ::/96         4
label fec0::/10     5
label fc00::/7      6
label 2001:0::/32   7

```

Microsoft has [kb-article]("http://support.microsoft.com/kb/2533454") describing what to do if you are broken. It would be nice if Ubuntu had a similar page.

---

### Post by novinick on 2011-05-27
what no body is saying is that ipv6 
makes every computer in lan  exposed to internet
this relates to all os/es, windows too is insecured

what are protective measures?

---

### Post by Cybjit on 2011-05-27
> **novinick said:**
> what no body is saying is that ipv6 
makes every computer in lan  exposed to internet
this relates to all os/es, windows too is insecured

what are protective measures?
A lot of people consider reachability a feature rather than a bug. But if you want to break IPv6 in a similar way to IPv4 NAT, you are welcome to install a stateful IPv6 firewall.

---

### Post by novinick on 2011-06-07
[LEFT]tomorow is , aparently that day, here's simple test
[http://test-ipv6.com/](http://test-ipv6.com/)
about ipv6 day
[http://test-ipv6.com/ipv6day.html](http://test-ipv6.com/ipv6day.html)
[http://server3.test-ipv6.com/faq.html](http://server3.test-ipv6.com/faq.html)

what if you have broken dual stack
[http://server3.test-ipv6.com/broken.html](http://server3.test-ipv6.com/broken.html)
[http://ds.test-ipv6.com/faq_6to4.html](http://ds.test-ipv6.com/faq_6to4.html)
or try to set mtu to 1400 or 1280

for ex.
```

ifconfig sit0 mtu 1400 up

```or, not really sure....
```
ifconfig tun6to4 mtu 1400 up
```**Setting up 6to4 router for IPv6**
[http://ubuntuforums.org/showthread.php?t=1684183](http://ubuntuforums.org/showthread.php?t=1684183)

frefox addon that is showing current used adress 
for current  page in status bar , for 6 is green
( use rc3, down in yellow download box for firefox4 )
[https://addons.mozilla.org/en-us/firefox/addon/showip/](https://addons.mozilla.org/en-us/firefox/addon/showip/)
[/LEFT]

---

### Post by novinick on 2011-06-07
first i would like to thank for great post, that sumarizes this issues :popcorn:
> **lemming465 said:**
> 



c) mediocre - use 6to4 anycast tunneling.  This requires protocol-41 support and a public, non-RFC-1918, IP address.  Failure rates on IPv6 connections can be as high as 15% and latency will be bad.  My favorite 6to4 setup script is from [New Zealand ISP anyweb]("http://www.anyweb.co.nz/tutorial/Linux6to4Host")


about newzealand script...
this script seems to work if you have ipv4 direct on eth0 or ppp or other device

not behind ipv4 routers

by small modification this makes it possible too, with some minor isues
at least all is green on ipv6 test (in attachment) :

also if you get to have some DNS probs ,change dns adreses there are several options
 
really was having fun this time :lolflag:
also there exist some whitelsist out there  :confused: so not ipv6 all servicess will be accesibile

---

### Post by lemming465 on 2011-06-07
> not behind ipv4 routers
Correct, if you are on a private IP address such as 192.168.x.y behind a NAT44 router, you can't use a 6to4 tunnel.  The relays for 6to4 tunnels use the 2002:*p.q.r.s*::/48 prefix on your IPv6 address to send IPv4 packets back to you with IPv6 payloads.  That means p.q.r.s has to be a public IPv4 address.  On private addresses you either need a highly cooperative router or a different tunneling protocol entirely such as "6in4" (point to point) or "teredo" (UDP encapsulated and designed for NAT traversal).

> ... not ipv6 all services will be accessible
True, but the point of world IPv6 test day (starting in about 3 hours) is to have more of them be accessible.  Things that can go wrong include:

* bad IPv6 connectivity - not all internet backbone providers have good routing to the entire IPv6 internet.  Quick and dirty test: does your ISP peer with Hurricane Electric on IPv6?  Yes and you are in pretty good shape; no and you may have to worry.

* bad DNS - if your ISP doesn't query AAAA records, or returns bogus parking site answers for AAAA queries, you may not connect correctly to sites with do advertise AAAA, or even to sites which don't.

* bad firewall / wifi / broadband gear - if your dual-stack Linux or windows-7 or OS-X 10.6.5+ client tries to reach an IPv6 site via some native or tunneled connection, but something in the middle hates native IPv6 packets (ethernet type 0x86dd) or hates the tunneling protocol (e.g. #41, IP in IP; or #47 Generic Router Encapsulation) or hates the destination address or port (192.88.99.1 for 6to4; udp/3544 for Teredo servers), you are out of luck.

* IPv6 overload - the ISP or content provider is running equipment which doesn't have feature parity with IPv4 for performance, and collapses under the v6 load

With 400+ major sites including Google, Youtube, Facebook, Yahoo, Microsoft, CNN etc. all about to go dual-stack, it is a Really Great Day to be experimenting with IPv6.  You'll have so much more of it than usual to play with.

---

### Post by novinick on 2011-06-07
Yes, great day ;)

What i'm trying to say , i've managed to conect from behind router
( think it works under testing conditions , only one computer in soho network )

by modifying newzeland script at this places
```

       # We simply take the device from the first default route
       ** CUR_RTR_IP=**(`ip -4 addr show ${CUR_DV} | awk '/inet / { print $2 }' | \
               sed -e 's/^\(\([0-9]\{1,3\}\.\)\{3\}[0-9]\{1,3\}\).*$/\1/'`)
        **CUR_IP=(`curl http://www.whatismyip.org/`)**

        # Find the MTU on the interface used for the tunnel
        DEV_MTU=`ip link show ${CUR_DV} | tr '\n' ' ' | \
                                          sed 's/.* mtu \([0-9]\+\).*$/\1/'`

        # Multiple IP addresses may be defined on device. First one is ours.
        # Add the tunnel. The local address is the one found from default route.
        ip tunnel add ${TUN_INTF} mode sit remote any local **${CUR_RTR_IP}**
        # Bring the tunnel up.
        ip link set dev ${TUN_INTF} mtu `expr ${DEV_MTU} **- 80`** up
        # Add the interface address
        IPV6_ADDR=$(printf "2002:%02x%02x:%02x%02x:%04x::%04x" \
                  $(echo "${CUR_IP} ${SLA_INTF} ${INTF_ID}" | tr '.' ' '))
        ip -6 addr add ${IPV6_ADDR}/${INTF_PFX} dev ${TUN_INTF}

```Where public ip is now being read from outside, and mtu is little lower
Kudos to nz for documenting script :popcorn:

---

### Post by jtarin on 2011-06-08
I got this in my email:```
Hi Folks.  You have probably heard that today is World IPv6 Day, with
sites like Google, Facebook, and Yahoo publishing IPv6 records for
their main web sites.  I'm happy to report that the Nmap Project is
celebrating in several ways:

==Scanme Updated to IPv6==

You probably know that we run the machine scanme.nmap.org as a system
people are allowed to use as a target for test scans and the like.
That system now has native IPv6 support.  So if you have never
performed an IPv6 port scan, you can do so with a command like:

nmap -6 -v scanme.nmap.org

We also added a DNS record for scanmev6.nmap.org, which only has an
IPv6 address (no IPv4).  This can help for tools which might otherwise
use Scanme's IPv4 address by default rather than IPv6.  For example,
you can insure that your web browser is connecting to the IPv6 version
of the Scanme web site by visiting:

http://scanmev6.nmap.org/

You might expect that to fail if you haven't done any IPv6 setup, but
you might be surprised!  Many operating systems can automatically set
up various types of IPv6 tunnels as needed.  Give it a try!

==Nmap Web Sites==

All of our main web sites (Nmap.Org, Insecure.Org, SecLists.Org,
SecTools.Org) are now reachable by IPv6.

I've noticed that some other participants have been using "vanity"
IPv6 addresses:

www.facebook.com - 2620:0:1c18:0:face:b00c::
www.cisco.com - 2001:420:80:1:c:15c0:d06:f00d
www.bbc.co.uk - 2001:4b10:bbc::2

So we're proud to fly our 2600 flag!

nmap.org - 2600:3c01::f03c:91ff:fe96:967c

Admittedly that is a coincidence, but we're still happy about it :).

==Nmap Code==

We're not announcing the incorporation of IPv6 support into Nmap today
for one reason: we already did that in 2002 :).  Just add the -6
option to your command. Basic TCP port scanning and host discovery were
added back then, and we included IPv6 support for newer features such
as version detection, Ncat, and the Nmap Scripting Engine as they were
released.

While Nmap has long included basic IPv6 support, there have been
important limitations.  In particular, raw packet scans (SYN scan, UDP
scan, ICMP ping packets, etc.) and traceroute were not supported.  I'm
happy to announce that we removed those limitation today!  You can
find details and download URLs for our special IPv6 test release (Nmap
5.52.IPv6.Beta2) here:

http://seclists.org/nmap-dev/2011/q2/866

IPv6 OS detection isn't included yet, but we're working hard on it!

Even if you aren't interested in the IPv6 support for some reason,
that release includes many other new features that haven't made it to
a general release yet.

Enjoy the new code and web sites, and I'd like to wish every one of
you a very happy IPv6 Day!  May your scans be lightning quick and your
IPv6 configuration secure!

Cheers,
Fyodor
```

---

### Post by novinick on 2011-06-09
hi

On the ipv6 day , my linux system seem's to have
been prefering ipv6 tuneled connection, when browsing sites. :popcorn: (which was bit slower then native but still was prefering it)

I suspect that was been configured on servers it self to prefer or force v6 for greater efectivness of that day. 
> Note that for dual-stack web sites most operating systems will prefer native connections to 6to4 or Teredo tunnels, so on world IPv6 day you would mostly be using IPv4 anyway. To force IPv6, you can either tune /etc/gai.conf, which is complicated, or put raw IPv6 addresses into URL's in square brackets, e.g.

---

### Post by lemming465 on 2011-06-10
By any chance were you using a point-to-point tunnel (aka "6in4")?  From the point of view of getaddrinfo(3) and the ipv6 routing table, that looks more like full native connectivity, and v6 would be preferred to v4 for dual-stack destinations.

---

### Post by novinick on 2011-06-11
no it was 6to4 i think by using nz script or modification

or this way , i knew that was from somewhere ;)
[http://ubuntuforums.org/showthread.php?t=1752125](http://ubuntuforums.org/showthread.php?t=1752125)

i was watching youtube and all connections but one or two were 200x:something
as mesured by iptraf.

may have diferent behaviour ,this networking 
between previous kernels/utilities and latest, and perhaps 64bit systems
and perhaps difers from distribution to distribution.

---

