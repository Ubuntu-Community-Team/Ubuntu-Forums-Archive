---
title: "Strange bind9 DNS problems"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by maclover201 on 2010-03-21
I've been setting up a DNS server for my network. My router at 10.0.0.1 (running DD-WRT, of course) assigns three DNS servers to the clients:
10.0.0.20 (Ubuntu Server DNS)
208.67.222.222 (OpenDNS)
208.67.220.220 (OpenDNS)

...with domain jones.cc.

The problem I'm experiencing is that the servers tatooine.jones.cc (10.0.0.20) and hoth.jones.cc (10.0.0.22) (hooray Star Wars references) can resolve the IP of other servers on the domain properly, whereas clients cannot for some odd reason.

For example, here's the ping output from Tatooine pinging one of the wireless APs, Coruscant:
```
root@tatooine:/# ping coruscant.jones.cc
PING coruscant.jones.cc (10.0.0.2) 56(84) bytes of data.
64 bytes from coruscant.jones.cc (10.0.0.2): icmp_seq=1 ttl=64 time=0.637 ms
64 bytes from coruscant.jones.cc (10.0.0.2): icmp_seq=2 ttl=64 time=0.680 ms
64 bytes from coruscant.jones.cc (10.0.0.2): icmp_seq=3 ttl=64 time=0.654 ms
^C
--- coruscant.jones.cc ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 0.637/0.657/0.680/0.017 ms
```

Works fine. For reference, here's Tatooine's resolv.conf file.
```
domain jones.cc
search jones.cc
nameserver 10.0.0.20
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Also, here's the output from nslookup on Hoth. The output is the same on Tatooine.
```
root@hoth:~# nslookup coruscant
Server:		10.0.0.20
Address:	10.0.0.20#53

Name:	coruscant.jones.cc
Address: 10.0.0.2
```

Everything works the same on Hoth, my other server which is going to be set up for load balancing in the near future.

Anyway... here's the ping output from a client, even after flushing DNS cache and everything. If you were wondering, it is being assigned the right domain and DNS servers in the right order.

```
morgan-mbp:~ Morgan$ ping coruscant
PING coruscant.jones.cc (67.215.65.132): 56 data bytes
64 bytes from 67.215.65.132: icmp_seq=0 ttl=55 time=27.107 ms
64 bytes from 67.215.65.132: icmp_seq=1 ttl=55 time=51.750 ms
64 bytes from 67.215.65.132: icmp_seq=2 ttl=55 time=27.878 ms
^C
--- coruscant.jones.cc ping statistics ---
3 packets transmitted, 3 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 27.107/35.578/51.750/11.439 ms
```

And this client's nslookup output. It's the right address and everything, why is traffic being redirected to that external IP? I did a reverse lookup, that IP corresponds to hit-nxdomain.opendns.com. I have no idea why it needed to resolve that IP if Tatooine already resolved it properly.

```
morgan-mbp:~ Morgan$ nslookup coruscant.jones.cc
Server:		10.0.0.20
Address:	10.0.0.20#53

Name:	coruscant.jones.cc
Address: 10.0.0.2
```

What's going on?! Here are my zone configurations for bind9. Enjoy Star Wars fanboys.

```
; Options
$TTL 604800
@         IN SOA ns.jones.cc. root.jones.cc. (
	             2010032103		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL

; General DNS Config
@ IN NS    ns.jones.cc.
IN MX 10 mail.jones.cc.
jones.cc. IN A 10.0.0.20

; Server 1 (Tatooine)
@        IN A   10.0.0.20
tatooine IN A   10.0.0.20
ns       IN A   10.0.0.20
mail     IN A   10.0.0.20
www      IN A   10.0.0.20

; Server 1 iLO (Dagobah)
dagobah  IN A  10.0.0.21

; Server 2 (Hoth)
hoth     IN A  10.0.0.22

; All APs, routers, etc
naboo     IN A  10.0.0.1
coruscant IN A  10.0.0.2
alderaan  IN A  10.0.0.3
endor     IN A  10.0.0.4

; Printers
yoda      IN A 10.0.0.10
vader     IN A 10.0.0.11
skywalker IN A 10.0.0.12
```

Here's the reverse lookup zone.

```
$TTL 604800
; Options
@         IN SOA ns.jones.cc. root.jones.cc. (
                     2010032105         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL

; Nameservers
@ IN NS ns.
20 IN PTR jones.cc.
20 IN PTR ns.jones.cc.
20 IN PTR mail.jones.cc.
20 IN PTR www.jones.cc.
20 IN PTR tatooine.jones.cc.
21 IN PTR dagobah.jones.cc.
22 IN PTR hoth.jones.cc.
1  IN PTR naboo.jones.cc.
2  IN PTR coruscant.jones.cc.
3  IN PTR alderaan.jones.cc.
4  IN PTR endor.jones.cc.
10 IN PTR yoda.jones.cc.
11 IN PTR vader.jones.cc.
12 IN PTR skywalker.jones.cc.
```

Help would be appreciated. If I have any weird misconfigurations please let me know.
Morgan

---

### Post by jrssystemsnet on 2010-03-21
The problem is, you're trying to hijack a real domain (jones.cc) and you have real nameservers in the mix in your resolvers.  You haven't actually shown what the resolver info in your clients is, but if it looks like this:

> domain jones.cc
search jones.cc
nameserver 10.0.0.20
nameserver 208.67.222.222
nameserver 208.67.220.220

Then your problem is unsurprising in the extreme.

If you're going to hijack real domain names for your private use, you CAN'T refer to real nameservers in your resolver info for clients; you have to have them use your local fake DNS and nothing but.

---

### Post by maclover201 on 2010-03-21
Oh. I see now, thank you. I was expecting it to be a misconfiguration or something. Spot on, I checked my resolv.conf on one of my Mac OS clients and it looks like this:

```
domain jones.cc
nameserver 10.0.0.20
nameserver 208.67.222.222
nameserver 208.67.220.220
```

If I have my clients only use 10.0.0.20 as their DNS server, I could get the benefits of OpenDNS for non jones.cc domains by setting my forwarders in named.conf.options, correct?

```
forwarders {
208.67.222.222;
208.67.220.220;
};
```

Thanks for the advice.

Morgan

---

### Post by jrssystemsnet on 2010-03-21
> **maclover201 said:**
> If I have my clients only use 10.0.0.20 as their DNS server, I could get the benefits of OpenDNS for non jones.cc domains by setting my forwarders in named.conf.options, correct?

```
forwarders {
208.67.222.222;
208.67.220.220;
};
```

Yep, that's the correct way to do it (and anyway, you should pretty much **always** try to have forwarders available for any small nameserver, to avoid unnecessary load on the root servers).

Also, however, I would strongly advise you to not hijack real public domain names for intranet use.  Just use .local as the TLD; that way you won't have conflicts like this (and nobody will get confused about whether they're on a public or a private site, to boot).

---

### Post by maclover201 on 2010-03-21
Good point. I will consider that. If I set my forwarders for bind9 as the OpenDNS servers, do I need to assign a second and a third DNS entry to the clients? Also, if I set my second server up as a slave of the first server through bind9 configuration, will that need to be the second DNS entry?

Thanks for your advice. Good catch on the jones.cc thing.

Morgan

---

### Post by jrssystemsnet on 2010-03-21
You only need multiple DNS resolver entries in the clients if you want them to be able to continue resolving DNS if the primary resolver is down.  If you expect your primary resolver always to be up, you can feel free to only have the one entry in client resolver configuration.

If you do set up a slave, then yes, the slave is what you'd want to be the second entry in clients.  Note, however, that for most small networks, the value of having a slave is minimal to none... it's entirely possible to have conflicts between a master and a slave DNS provider, where the slave doesn't immediately pick up on changes you made to the master.  You may find that it's not really worth it to try to run a master/slave DNS setup - you might decide to just run the single DNS provider and have done with it, or you might decide to instead run two masters, but simply manually keep the zones synchronized between them so that you *know* what's going on.

The master/slave setup makes more sense for really, really LARGE dns providers that have to respond to hundreds of thousands or millions of clients.  In a small network, or even in authoritative servers for most public domains, DNS load is laughably small no matter what you do, so trying to do the traditional master/slave setup becomes more of an administrative pain than it's worth.

---

### Post by maclover201 on 2010-03-21
Ok, I see. So if I set up the OpenDNS forwarders in bind9, I won't have to include them in the client configuration.

... right?

---

### Post by jrssystemsnet on 2010-03-21
Correct.  Your clients will ask your bind9 server for ALL dns resolution, whether local or not; your bind9 server will resolve anything you've defined zones for authoritatively, and will answer all *other* requests by relaying the request on to its forwarders and then passing the answers back to the client.

Something worth noting: even without defining the forwarders, it would have behaved this way... but it would have been asking the root servers for the internet, getting NS answers from them, then going off to the authoritative NS for the domain in question, getting the answer to the original resolution query from THEM, then passing THAT on to your client.

So, your bind9 server answers the client for anything and everything either way... but it does so in a much more friendly-to-the-infrastructure-of-the-internet way when you have forwarders configured in the conf file.  (Because it will take advantage of the cache in those forwarders, to greatly reduce the load on the lower-level infrastructure.)

---

### Post by jrssystemsnet on 2010-03-21
Also worth noting: this way your bind9 server also caches the answers for your client locally to *it*; so the first time a client asks how to get to google.com, your bind9 server asks the OpenDNS servers, they answer, and it passes the answer back to your client.  The *second* time a client asks how to get to Google.com, your bind9 server serves the query from cache, so it never has to leave your network.

---

### Post by maclover201 on 2010-03-21
Awesome. Thanks for the information.
Just making sure as well, I can use any TLD not on [http://en.wikipedia.org/wiki/List_of_Internet_top-level_domains](http://en.wikipedia.org/wiki/List_of_Internet_top-level_domains) for the local TLD, right?

---

### Post by maclover201 on 2010-03-21
Right, that was one of the reasons I set up bind9. It will overall make the entire network's DNS queries faster if set up properly.

---

### Post by jrssystemsnet on 2010-03-21
Sure; although keep in mind that sometimes new TLDs get added.  ".local" is unlikely in the extreme to ever be a public TLD. :)

Also keep in mind you don't really have to use a separate TLD at all - an intranet domain is effectively a TLD of its own regardless; there's nothing keeping you from just declaring "jones" as the TLD, and having hosts at tattooine.jones, hoth.jones, etc.  And having the intranet site, if there is one, at [http://jones](http://jones).

---

### Post by maclover201 on 2010-03-21
Cool, just updated my config, set up my slave server, and everything's working great. How can I make sure bind9 is actually caching requests?

---

### Post by jrssystemsnet on 2010-03-21
> **maclover201 said:**
> How can I make sure bind9 is actually caching requests?

```
me@banshee:~$ dig @192.168.0.5 espn.com | grep -A 1 ANSWER\ S
;; ANSWER SECTION:
espn.com.		900	IN	A	199.181.132.250
me@banshee:~$ sleep 5
me@banshee:~$ dig @192.168.0.5 espn.com | grep -A 1 ANSWER\ S
;; ANSWER SECTION:
espn.com.		893	IN	A	199.181.132.250
```

Use the **dig** command to see that the TTL for the answer is decreasing.  In this instance, I asked a bind server at the address 192.168.0.2 for information on espn.com (and filtered the results through grep to make reading this easier for you), waited 5 seconds, then asked again.

You can see that the initial TTL for the record is 900 seconds, and that it's down to 893 seconds (in between the 5 second **sleep**, and how long it takes me to type stuff) when I dig my server a second time.  So, I know that my server cached the result of the first query, and will keep that cached result for another 893 seconds.  After 893 seconds, the cached result has expired, so my server will discard it and inquire anew if I ask it again.

---

### Post by maclover201 on 2010-03-21
Cool, it's really working for me. Thanks for your help!

---

