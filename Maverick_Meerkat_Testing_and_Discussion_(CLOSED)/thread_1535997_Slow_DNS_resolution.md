---
title: "Slow DNS resolution"
date: 2010-07-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by JCoster on 2010-07-21
I know this is a problem which has plagued Ubuntu/Debian-based installs for a while now but recently my DNS has been absolutely awful.

In Chrome, it shows 'resolving host' for over 5 seconds for each site.  Same in Firefox with 'lookup up host.'

I'm running Karmic in VirtualBox with a bridged adaptor with Chrome and there are no problems whatsoever..  I can start loading a page on the host, then start loading it on the guest and the guest beats the host by a long way.

I've tried disabling IPv6 and have removed 'DNS pre-fetching' in Chrome but I've had no luck.

I'm using the Google DNS servers on both Ubuntu and my router.  I've tried OpenDNS too but neither are any better so I don't think it's a server problem.

Anyone got any ideas?

Cheers,
JC

EDIT: Posting that took over 15 seconds and I'm on 12mb broadband...

---

### Post by endotherm on 2010-07-21
last time I had that issue, a poorly behaving torrent client was causing too many half formed tcp connections coming into my router, and the router was not purging them quickly enough, so even though utilization of bandwidth was low, the router was still bogged down. what other services do you have running?

---

### Post by sisyphus1978 on 2010-07-21
I noticed seriously slow browsing yesterday. I was using google dns. Now I am using my broadband supplier's dns (with opendns and google as back ups). It is now back to normal.

I suggest try another dns service.

I'm using lucid btw, but thought you might like the tip.

---

### Post by JCoster on 2010-07-21
Cheers for your quick reply.

However, I have no services out of the ordinary running... and it does it from start-up.

Just a thought though, I do have apache running so I'll try removing that and see if that helps at all.

Any other ideas?

Cheers,
JC

---

### Post by cariboo on 2010-07-21
You may want to try manually entering dns addresses in Network-Manager.

---

### Post by BobCFC on 2010-07-22
This just started happening to me today too.

I get an instant response if I ping the google DNS server ( 8.8.8.8 ) but chrome says Resolving Host relentlessly

Surfing is fine once it knows the address though, and other non web services are fine.

---

### Post by JCoster on 2010-07-22
Cheers for your responses.
DNS settings are manually set in network-manager as well as my router.

BobCFC, I'm sorry to hear you're having the same problem.  Are you experiencing long lookups in Firefox as well?  

I'm very close to giving up and doing a reinstall..
JC

UPDATE: It may be worth adding that performing an 'nslookup' on a domain retrieves the IP almost immediately, so it must be linked to the browsers only?

---

### Post by endotherm on 2010-07-22
> **JCoster said:**
> 

UPDATE: It may be worth adding that performing an 'nslookup' on a domain retrieves the IP almost immediately, so it must be linked to the browsers only?
it does seem like you are all using chrome and googles dns servers. is that correct?

---

### Post by JCoster on 2010-07-22
Yes, however, I have tested Firefox with OpenDNS and have had no change in speeds with that.

---

### Post by napp on 2010-07-22
Just registered as i'm having the exact same problem and just came across this thread. Everything been working fine for me but since the last few days I'm also experiencing the same issue.

Also using Google DNS, Ubuntu and Chrome. I've got a gut feeling that it might be related to a recent ubuntu update that was pushed out but can't be sure.

---

### Post by endotherm on 2010-07-22
> **napp said:**
> Just registered as i'm having the exact same problem and just came across this thread. Everything been working fine for me but since the last few days I'm also experiencing the same issue.

Also using Google DNS, Ubuntu and Chrome. I've got a gut feeling that it might be related to a recent ubuntu update that was pushed out but can't be sure.
or perhaps to the changes to the Root DNS Zone that were pushed out this last week (DNSSEC)

---

### Post by kyleabaker on 2010-07-22
I started noticing this a couple of weeks ago and I've been hoping it would resolve itself. I've got things setup with OpenDNS and haven't had any trouble with this (unchanged) setup in the past.

---

### Post by BobCFC on 2010-07-22
> **JCoster said:**
> Are you experiencing long lookups in Firefox as well?

Yes firefox says 'Looking up [www.something.com](www.something.com)' for ages just like chromium.  

> **endotherm said:**
> it does seem like you are all using chrome and googles dns servers. is that correct?

You are right! I switched back to full DHCP so that it used my ISP DNS instead of 8.8.8.8 and it is OK.  I wonder why I can ping 8.8.8.8 instantly but not use it as a DNS?


EDIT: I notice that it says my nameserver is my router/gateway now so maybe it is a subnet issue?

> **endotherm said:**
> or perhaps to the changes to the Root DNS Zone that were pushed out this last week (DNSSEC)

Also possible

---

### Post by psyke83 on 2010-07-22
Folks,

There are several discussions and bugs filed regarding slow DNS lookups.

I recommend you take a look at this thread on the ubuntu-devel-discuss mailing list:
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-May/011562.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-May/011562.html) (May posting)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-June/011565.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2010-June/011565.html) (beginning of June replies; click on "[thread]" link to see further replies)

Here's a related bug (I am sure there are others filed, though I don't have the numbers handy):
[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940)

The only real solution for me is to install and configure dnsmasq to cache DNS requests, and I hope that a caching server is included in the default install.

---

### Post by kyleabaker on 2010-07-22
> **psyke83 said:**
> The only real solution for me is to install and configure dnsmasq to cache DNS requests, and I hope that this gets included by default.

So, this is indeed an Ubuntu bug?

---

### Post by psyke83 on 2010-07-22
> **kyleabaker said:**
> So, this is indeed an Ubuntu bug?

I recommend that you read the bug report in its entirety. There is a resonably large consensus that avahi lookups cause DNS slowdowns for many users... but for others, simply disabling avahi lookups is not enough to prevent slowdowns (and other bugs may apply). Not to mention that disabling avahi causing a loss of functionality...

For me, installing dnsmasq on Ubuntu allows for fast lookups (as fast as Windows XP/7), without the need to disable the avahi daemon. The bug may still be present, but perhaps it gets mitigated by caching lookups.

---

### Post by kyleabaker on 2010-07-23
I think I've solved the problem on my end. I usually run update, upgrade, autoremove and clean from the terminal and for some reason autoremove didn't catch this...

I opened Synaptic and noticed that "libdns64" was listen in autoremove, so I closed Synaptic to see if the terminal just ignores it. Autoremove from the terminal failed to remove it.

So I opened Synaptic again removed it from there. Now everything seems to be fine. I'm wondering if this could be the same problem others are seeing? I now see "libdns66" installed, but it doesn't seem to be causing the same problem.

---

### Post by BobCFC on 2010-07-23
It was definitely the Google DNS - it happened to my dad's laptop at the same time and he is running stock Lucid

---

### Post by RJARRRPCGP on 2010-07-23
I'm having slow DNS resolution for a long time.

But it seems to be less bad with Chromium 6x.

---

### Post by diebels on 2010-07-23
I vote for a caching server in the default install.  It can make a tremendous difference to surfing speed.  You can install dnsmasq and edit the connection to dhcp address only and 127.0.0.1 as dns server.  I use the following options in a file in the /etc/dnsmasq.d/ directory:
```
cache-size=9000
listen-address=127.0.0.1
no-dhcp-interface=127.0.0.1
bind-interfaces
server=8.8.8.8
server=8.8.4.4

```

---

### Post by Imran-UK on 2010-07-23
I've noticed slow internet browsing all this week. Today I had enough and called my ISP (Be Broadband UK). We went through troubleshooting and I mentioned that I was using Google DNS. The support guy told me that he's been hearing many other customers on Google DNS reporting slow internet. I changed back to the ISP default nameservers and internet speed was back to normal. I think Google DNS has recently just become overloaded, like it's reached a tipping point in popularity or something. Unlike a hostname, an IP cannot be load-balanced as efficiently I don't think.

I run a SheevaPlug with Debian on my LAN and intend to use the Bind9 install on that as a caching nameserver.

Router:
```
imran@imran-desktop:~$ dig @192.168.98.1 www.google.com

;; Query time: 23 msec
;; SERVER: 192.168.98.1#53(192.168.98.1)
;; WHEN: Sat Jul 24 00:51:24 2010
;; MSG SIZE  rcvd: 172
```

Caching nameserver on SheevaPlug:
```
imran@imran-desktop:~$ dig @192.168.98.10 www.google.com

[B];; Query time: 1 msec
[/B];; SERVER: 192.168.98.10#53(192.168.98.10)
;; WHEN: Sat Jul 24 00:53:23 2010
;; MSG SIZE  rcvd: 244
```

Google DNS times out sometimes but otherwise is about the same as the router:
```
imran@imran-desktop:~$ dig @8.8.8.8 www.google.com

;; Query time: 27 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Sat Jul 24 00:54:27 2010
;; MSG SIZE  rcvd: 172
```

As someone suggested in a previous post, I would try running dnsmasq as a local caching nameserver and see what difference that makes to your internet speed (plus it's educational!). If you must use Google then I found better response from the secondary, 8.8.4.4

C'mon Google, leverage your massive infrastructure to cope with demand! :-)

---

