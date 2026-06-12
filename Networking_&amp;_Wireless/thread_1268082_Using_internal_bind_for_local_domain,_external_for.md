---
title: "Using internal bind for local domain, external for all else"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by frankvw on 2009-09-16
Hi, everyone!

I wonder what the default behavior of /etc/resolv.conf is with regard to multiple nameserver. For example, if /etc/resolv.conf has the following:

search domain.com
nameserver 127.0.0.1
nameserver 1.2.3.4
nameserver 5.6.7.8

does that mean that a DNS request is sent to 1.2.3.4 only if 127.0.0.1 does no accept it (e.g. times out, rejects the connection, or whatever) or will 1.2.3.4 also be queried if 127.0.0.1 accepted the request but could not resolve it?

Second, is it possible (and if so how) to make bind9 resolve an internal domain only and not go to the root servers for non-local domains?

What I am trying to do is this: on 127.0.0.1 I want to run bind9 to resolve an internal private domain ONLY but for all else external name servers should be used. I am on a connection that does allow fast access to the ISP's external DNSes, but running an internal DNS that then goes to the root servers to resolve what is not in its own zone files takes forever.

So... I need to stop bind9 from going to the root servers (in a way that does not involve timeouts) and I need to make sure that if my local bind9 doesn't have the domain in its zone files the request gets farmed out to the ISP's external DNS.

Problem is, I am not all that good with DNS and bind, and I don't really have much of a clue as to what I'm doing... :-)

All advise, suggestions and adult supervision would be appreciated.

Thanks!!

// FvW

---

### Post by yknivag on 2009-09-18
I'm no expert, but currently researching how to do something very similar.

From what I've gathered so far the easiest way to achieve this is to set the local DNS to resolve all queries for the local domain and then use the "forward" directive to send all other requests to your ISP's DNS.  That way the local DNS will only end up contacting the root servers if the name isn't resolvable locally or by your ISP (or your ISP's DNS is down).

It is also possible (though I know not how) to make the local DNS server cache requests for external addresses thus speeding up the whole process.

---

### Post by frankvw on 2009-09-21
> **yknivag said:**
> set the local DNS to resolve all queries for the local domain and then use the "forward" directive to send all other requests to your ISP's DNS.

That sounds exactly like the solution I'm looking for. However, the million dollar question is now: how do I do that, starting from the stock bind9 config in my Ubuntu Jaunty install?

// FvW

---

### Post by yknivag on 2009-09-23
If I knew that, I'd have it running here. I'm sure there must be someone here who does though!

---

### Post by frankvw on 2009-09-25
> **yknivag said:**
> If I knew that, I'd have it running here. I'm sure there must be someone here who does though!

So let him or her step forward! :-)

// FvW

---

### Post by rngresearch on 2011-06-22
> **frankvw said:**
> So let him or her step forward! :-)

// FvW

If you configure bind to use "forwarders", it will "farm out" queries that it cannot answer with it's own zone data to those forwarder(s).  It also caches the replies.
Referring to /etc/bind/named.conf (I'm running debian, so this might be elsewhere with ubuntu.),
it includes the file /etc/bind/named.conf.options, which looks like this out of the box:
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

    // forwarders {
    //     0.0.0.0;
    // };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
```Importantly, you should note that _There can be only one_ "options { ... }" declaration in the entire configuration, including all included files.  A second declaration will not augment/replace options; it will result in an error.  Also, as you probably already know, the syntax for adding, say, two nameservers, would be:
```
options {
    // your other options
    forwarders {
        123.45.67.89;
        98.76.54.32;
    };
    // your other other options
};
```

---

