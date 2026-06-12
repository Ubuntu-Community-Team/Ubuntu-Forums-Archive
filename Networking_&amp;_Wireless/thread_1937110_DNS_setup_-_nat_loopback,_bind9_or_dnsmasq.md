---
title: "DNS setup - nat loopback, bind9 or dnsmasq?"
date: 2012-03-07
forum: Networking &amp; Wireless
---

### Post by d2a on 2012-03-07
Ok - I have a very messy home network as follows:

ADSL Modem/wireless router/switch

Various devices connect via wireless and use DHCP to obtain IPs

A desktop with a fixed IP connects via powerline ethernet

A media box running ubuntu 10.04 with a fixed IP connects via a wifi ethernet adapter which also has a fixed IP

Finally, a server running ubuntu 10.04 with a fixed IP which hosts a mailserver, and connects via powerline ethernet. this mailserver is accessed via a domain from outside the LAN.

Phew :D

I'm hoping to simplify this setup slightly, by moving the mail server onto the media box, and killing off the other server. As part of this move, I'm trying to install a dns solution, so that I can use the same domain to access the mailserver when I'm connected via wifi within the LAN.

I am able to use NAT loopback on the router at the moment, but I believe this isn't the best option, and that a home DNS server would do a better job. I have installed bind9 on the media server to test, and managed to get something working but it was not stable - many DNS requests timed out.

I configured the router to supply the ip of the mediaserver as DNS to clients connected via DHCP, and the mediaserver has my ISPs DNSservers added as forwarders.

Does anyone know a more elegant solution to the problem - I can't be the only person hitting this wall can I? Thanks for any help...

---

### Post by Derek Karpinski on 2012-03-08
Is your router capable of being flashed with dd-wrt? If so, you could set your router to deal with DNS via built in dnsmasq, DHCP, etc.  dd-wrt is basically a very lightweight linux distro for routers.
 
It's really a powerful setup that I'd recomment to anyone.
 
Check here to see if your router can run it........and follow instructions to the 'T' if you decide to flash it with dd-wrt.
 
[http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)

---

### Post by d2a on 2012-03-20
thanks for the suggestion. My router isn't capable of running 3rd party firmware unfortunately. Is this really an unusual situation? I'd have thought lots of people who run home servers would need to have local access via a domain, but perhaps I'm missing something really obvious. I suppose if i have to i can just host my mail server off-site...

---

### Post by SeijiSensei on 2012-03-20
> **d2a said:**
> I have installed bind9 on the media server to test, and managed to get something working but it was not stable - many DNS requests timed out.

Can you resolve names on the box itself using the localhost interface?  What happens if you use the command "host hostname localhost" on that box, replacing "hostname" with the name of a host you have entered into the zone file for your domain?  Do you get the proper reply?

Now try "host hostname 1.2.3.4" replacing "1.2.3.4" with the external IP address of the server (the address you're handing out to clients).  Does that work?  If not, check the "listen-on" directive in /etc/named.conf to make sure that bind is listening on all interfaces, not just localhost (127.0.0.1).

What kinds of errors do you see in /var/log/syslog?

---

### Post by d2a on 2012-03-20
Thanks for the reply

```
host studio.mydomain.com localhost
Using domain server:
Name: localhost
Address: 127.0.0.1#53
Aliases: 

studio.mydomain.com has address 192.168.1.16
```

then

```
host studio.mydomain.com 192.168.1.21
Using domain server:
Name: 192.168.1.21
Address: 192.168.1.21#53
Aliases: 

studio.mydomain.com has address 192.168.1.16

```

where studio.mydomain.com is the domain set up for internal and external use, 192.168.1.16 is the mailserver's fixed IP, and 192.168.1.21 is the fixed IP of the media server hosting the bind DNS.

I will leave this setup for a while and capture some errors...

---

### Post by d2a on 2012-03-20
intermittent syslog errors look like this (domain is just an example, any domain can have the issue):

```
named[2915]: error (network unreachable) resolving 'news.bbc.co.uk/A/IN': 2001:dc3::35#53
```

and

```
named[2915]: success resolving 's.youtube.com/A' (in 'youtube.com'?) after disabling EDNS
```

additionally, intermittent fails such as:

```
host ubuntuforums.org 192.168.1.21
;; connection timed out; no servers could be reached
```




does that give any clues? If not, let me know if there's any log that might, and thanks for your time.

---

### Post by SeijiSensei on 2012-03-20
My guess is that the box is behind a firewall router that is blocking UDP traffic between your server and the roots over port 53.

One possibility is to add 

```

forward only;
forwarders { ip.of.isp.nameserver; ip.of.another.nameserver; };

```

to the options{} stanza at the top of the file.  This tells bind to forward any requests for which it isn't authoritative to the(se) other server(s) for resolution.  You can have multiple nameservers in the list to protect against the first of them being unavailable.  bind9 will try the servers in order.

Before you do this, check that you can resolve names against the ISP servers from behind your firewall with "host [www.google.com](www.google.com) ip.of.isp.nameserver".  You may find this fails as well.

If so, you might be able to forward requests to the router's internal address.  Many firewall routers maintain a small DNS server that is pre-configured to forward requests to the ISP.  These routers build up a cache of local names they collect from DHCP requests and send any other queries off to the ISP.  So if you can't talk directly to external nameservers, try forwarding requests to the router instead.  Again, use the "host [www.google.com](www.google.com) ip.of.your.router" approach to test whether this will work.

---

### Post by d2a on 2012-03-20
hmm - ok. i've already got the isps nameservers added as forwarders in /etc/bind/named.conf.options, within the options block as follows:

```
options{
        directory "/var/cache/bind";
        forwarders {
                isp.dns.com;
                isp.dns2.com;
        };
        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };

};
```

i've added the forward only; (i changed it from forward-only; as that made bind error) and i'm checking it now - looks quite promising!

---

### Post by SeijiSensei on 2012-03-20
> **d2a said:**
> i've added the forward only; (i changed it from forward-only; as that made bind error) and i'm checking it now - looks quite promising!

Whoops, sorry about that.  There are so many directives in the named.conf file that I have a hard time remembering the exact syntax of each!  Glad to hear you think you're making progress.

---

### Post by d2a on 2012-03-21
thanks - only took me a second to check it but i'd never of thought of putting it in if you hadn't mentioned it. this is looking pretty stable right now. I'm going to keep monitoring it but it's at least usable now.

Whilst I'm here, is this now forwarding all DNS requests except the custom zone specified to my ISPs dns servers, or is it building a cache and acting as a local DNS? IF the second case is true, I should expect small delays when requesting any new URL, but subsequently quicker lookups right?

---

### Post by SeijiSensei on 2012-03-21
Yes, it will cache lookups, though to be honest the difference in speed is probably in the millisecond range depending on the speed of your Internet connection.  It should resolve names in your local domains using the zone files defined in named.conf and forward any other requests to the ISP's servers.

Glad to hear that it's working correctly for you now!

---

### Post by jdthood on 2013-01-06
Anyone interested in having bind9's forwarders list dynamically updated, please add your voice to the following (wishlist) bug report.

    [https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602)

---

