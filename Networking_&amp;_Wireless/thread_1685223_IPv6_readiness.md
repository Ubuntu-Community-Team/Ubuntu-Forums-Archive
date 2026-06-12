---
title: "IPv6 readiness"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by JFekete9076 on 2011-02-10
Hello.

I've heard about the exhaustion of IPv4 addresses, and I roughly know what IPv6 is.

Does anyone know how to check whether our hardware (network adapters, routers, etc.), and software (operating systems, browsers, etc.) are ready for the transition?

Thanks in advance.

---

### Post by matrixflow on 2011-02-10
> **JFekete9076 said:**
> Hello.

I've heard about the exhaustion of IPv4 addresses, and I roughly know what IPv6 is.

Does anyone know how to check whether our hardware (network adapters, routers, etc.), and software (operating systems, browsers, etc.) are ready for the transition?

Thanks in advance.

First, make sure that your ISP provides you with v6 connectivity, then go to [http://ipv6-test.com]("http://ipv6-test.com/") and do the connection test.

If it shows your v6 address and related infos, then you're onboard. :)

You may also have to enable it on your router if it doesn't work.

---

### Post by annoyingrob on 2011-02-10
My whole network runs dual stack with an IPv6 tunnel from Hurricane Electric.

Most (all?) operating systems these days have IPv6 functionality including Linux, Windows xp and newer, and Mac os X. Heck, even apple iOS4 and above is IPv6 functional even though they don't advertise the IPv6 address anywhere in the settings.

most low level hardware like switches and nics and such will also handle IPv6 with no issue. 

Routers are the problem, most don't. I know apple Airport Extremes do, as well as anything running DD-WRT or tomato. Personally I just use an old computer running linux to handle my IPv6 routing.

---

### Post by JFekete9076 on 2011-02-10
Which routers are IPv6-ready?
I am using TP-Link WR340GD, which was bought in 2010.

---

### Post by lemming465 on 2011-02-11
The transition from v4 to v6 is a lot like the transition from analog to digital TV; new gear all around to mostly get the same content.  The odds are high that your existing broadband modem and wifi router don't actually support v6 properly and will have to be replaced in 2012 or 2013.  Waiting is a good consumer move, as quantity, quality, and prices of v6-capable gear will be improving rapidly in the next 6-18 months.

Finding out if your current gear supports v6 takes some doing; look up the exact model on-line and see if it's mentioned as a supported feature.  If not, be pessimistic.  If you have access to administrative interfaces, see if they have any v6 features visible; if not, be pessimistic.  It's a fair amount of work to actually test for v6 if your ISP doesn't support it already, so that's probably not worth the effort.  If you can reflash a device with 3rd party firmware, and it has enough memory of the various types (flash, ram), a lot of the linux router firmwares such as dd-wrt have v6 support.

On the OS front I recommend being on recent software, so serious v6 folks want windows 7, this summer's Mac OS-X 10.7 "lion", Redhat 6, etc.  v6 support in recent versions of Ubuntu is pretty good.  All modern browsers support "dual-stack" operation of v4 or v6 in parallel, so you are OK there, too.

ISPs and hosting providers need to support v6 ASAP, as their business customers will be demanding it.  Businesses may or may not need to rush; if they have asian customers, asian supply chains, mobile customers, or government contracts they need to hurry on v6 support, at least for their outward facing services.  Note that in the US smartphones are outselling computers, and 4G smartphone rollouts are all dual-stack-lite, with native v6 only; their v4 support is legacy v4 over v6 tunnels to carrier NAT44 translators.  Which is why the likes of google, youtube, facebook, netflix and cnn are already dual-stacked.  Enthusiasts don't have to wait for their ISP's to offer native or near-native (6rd) v6; they can set up IPv6 over v4 tunnels, e.g. with hurricane electric's "tunnelbroker.net", sixxs, or gogo6.  The one gotcha there is that your wifi router has to pass protocol 41 (IP over IP) too, not just protocols 1,6,17 (ICMP, TCP, UDP).  I recommend point to point tunnels rather than 6to4 (not available to most home users behind NAT devices) or Teredo (only for masochists).

The likely timetable is: RIR's run out of most v4 in 2011, ISP's run out in 2012, the year of the IPocalypse is 2013 - when new v4 is hard to get but v6 availability is still problematic.  Widespread world-wide availability of v6 is probably 2015.  99% v6 traffic is probably 2017.  Tier-1 ISP's turning off v4 routing on the global internet backbone is probably 2020.  The last v4 device lingers till, say, 2036.

---

### Post by JFekete9076 on 2011-02-11
Thank you for the answer.

---

### Post by Morbius1 on 2011-02-11
> **lemming465 said:**
>   I recommend point to point tunnels rather than 6to4 (not available to most home users behind NAT devices) or Teredo (only for masochists).
And is Miredo the Linux equivalent of Teredo?
> The Teredo IPv6 tunneling protocol encapsulates IPv6 packets into UDP/IPv4
datagrams, to allow hosts behind NAT devices to access the IPv6 Internet.

Miredo is a Teredo client (as per RFC 4380): it can provide IPv6
connectivity to a dual-stack IPv6/IPv4 host even if it is located behind a
NAT. It can also operate as a Teredo relay which forwards IPv6 packets
between the IPv6 Internet and remote Teredo clients.I've just stated looking into this and am not sure how this works and was wondering about your thoughts.

---

### Post by Skaperen on 2011-02-11
One caveat with a dual-stack I have encountered.  If you set up IPv6 on your LAN, but do not have IPv6 connectivity, yet, you will get long waits during DNS lookup.  This is because Ubuntu enabled IPv6 in the resolver, which will cause it to query for AAAA records before falling back to A records.  If a site has no AAAA records, you wait until your resolver asks for A records.  This can be quick if the site's DNS answers negatively for the AAAA records quickly.  But any slowdown causes much longer waits because the resolver tries AAAA 2 or 3 times before trying A records.  If the site does not answer AAAA (some cases of this), then the delay can be significant (up to 30 seconds or so).  If the site gives a positive answer for AAAA records, then things go from bad to worse if you can't reach their IPv6 addressed host.  The resolver would get the IPv6 address, and the application will try to connect.  Since the resolver only asks for AAAA records, and gets them, that is all that the application gets.  It would have to ask the resolver specifically for IPv4 addresses as a fallback.  How the application handles this can vary.  Some may do very bad.

---

### Post by lemming465 on 2011-02-11
Yes, "miredo" is the ubuntu (and Fedora) client for the Teredo protocol; I should have mentioned that.  You operate it by (1) sudo aptitude install miredo  (2) check file /etc/default/miredo for *START_MIREDO=true* (3) sudo /etc/init.d/miredo start.  Points (2) and (3) are probably automatic on the install.

If you don't want Miredo resuming every time you reboot, you need to edit it to say START_MIREDO=false instead.  And to shut down tunneled IPv6, sudo /etc/init.d/miredo stop.

The Teredo protocol assumes that you are behind a NAT44 translator (firewall / router) which doesn't pass protocol 41, but will let UDP responses in if you have previously leaked UDP packets out.  Your Teredo client contacts a teredo server on well known port UDP 3544 and configures a special IPv6 address with the 2001:0::/32 teredo prefix, the v4 bits of your server, the v4 bits of your outside public IPv4 address upstream, your UDP origination port, and some random bits to reduce spoofing risks.  When you want to talk to a v6 peer on the v6 internet, your client contacts the teredo server, which locates a teredo relay for you.  Your actual v6 traffic goes back and forth via the relay, encapsulated many layers of headers: IPv4 header, UDP header, Teredo header, IPv6 packet.  Different IPv6 peers may need different relays, so if you visit some advertising and content-distribution heavy web site which has 200 sundry servers contributing to the overall page, you could have 200 relays involved.  In case of long-lived TCP connections, to keep the UDP holes open through your NAT44 device, you send keep-alive UDP packets to your server and to all recently used relays every thirty seconds.

The good news: practically anyone can use Teredo to participate in the v6 internet, even when their ISP doesn't support native v6 and their modem and router gear doesn't support v6 either.
The bad news: expect about a 15% failure rate reaching sites, the overhead is immense so throughput will suck, the latency is completely appalling, so time to load a complex page might be minutes, not seconds.  As an R&D ploy to gain experience with v6 and reach one or two simple v6-only sites, do try it.  Do not delude yourself that it is fit for routine use; you would hate that.

On the bright side, having Teredo up probably won't cause the dual-DNS slowdown Skaperen describes, since /etc/gai.conf prioritizes native v4 ahead of tunneled Teredo.  There is a debate in the v6 community at present suggesting that the cutover from legacy v4 to our shiny new v6 might go more smoothly if web clients do DNS v6 (AAAA) and v4 (A) queries in parallel rather then serially, try to open both versions of a site, and only continue with whichever responds first.  Current web browsers and DNS resolver libraries don't do this, and the effects on internet congestion and server load would have to be dealt with, so who knows?

---

### Post by Morbius1 on 2011-02-11
Interesting. Thank you very much for your thoughts.

---

### Post by JFekete9076 on 2011-02-12
How much does Windows XP support IPv6?

---

### Post by lemming465 on 2011-02-12
You can run "*netsh interface ipv6 install*" and get a v6 stack that can send and receive packets.  I don't think it will do DHCPv6, and all the DNS queries are made over v4, so you can't run it as v6-only, not that you'd want to.  I suspect the multicast support may be below par, but don't actually know.  It probably won't be as aggressive about tunneling as windows 7, either.  Reports from places like ARIN which have run XP dual-stack with native v6 using stateless address autoconfiguration from the router advertisements say it works OK.

---

### Post by movieman on 2011-02-12
> **JFekete9076 said:**
> How much does Windows XP support IPv6?

Poorly, in my experience. It rejects some perfectly valid IP addresses, and doesn't support IPSEC; I don't know whether it works over the Internet as well as a LAN because we don't have IPV6 out of the house.

Edit: that said, I never managed to get IPSEC working over IPV6 in Ubuntu with Racoon either; it works fine with IPV4, but never seems to find the relevant configuration when it gets a request to set up a tunnel from an IPV6 address.

---

### Post by JFekete9076 on 2011-02-15
> **lemming465 said:**
> 
Finding out if your current gear supports v6 takes some doing; look up the exact model on-line and see if it's mentioned as a supported feature.


Can you suggest me a website for this?
I've been experiencing that it may be difficult to look for the specifications of a device.

---

### Post by lemming465 on 2011-02-15
Unfortunately, I'm not aware of any sites with good, up to date lists of which devices support v6.  Your best bet is to check the vendor site for your devices, and see if the technical specifications for your model mention v6.  Probably they don't, which you should interpret as "v4 only, no v6 support", and start making plans to replace them.  You have 1-4 years before that becomes a pressing issue, so there is no rush.

In the meantime, you can resort to v6 over v4 tunneling technologies such as 6in4 with a tunnel broker point to point link, or miredo.

---

### Post by JFekete9076 on 2011-02-15
I take your point. Anyway, I've been using Miredo for some days.

---

