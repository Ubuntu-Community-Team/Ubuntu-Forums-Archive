---
title: "Problems with DNS queries in OpenVPN tunnel"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by niglas on 2011-07-06
I set up a routed OpenVPN server. Everything works fine. But I'd like to route the DNS queries thru the tunnel too.

So I added:
```
push "redirect-gateway def1 bypass-dhcp"
```But the server did not seem to push out any DNS entries anyway, so I added:
```
push "dhcp-option DNS 10.8.0.9"
```(which is the default gw)

But the nslookup from the windows client gives:
```
*** Can't find server name for address 10.8.0.9: Timed out
```I tried pushing out 10.8.0.1 instead:
```
*** Can't find server name for address 10.8.0.1: Non-existent domain
```Even thou I have a DNS server set up correctly (on the same server as the VPN) with recursion.
I verified that by sending queries form external source, which worked fine.

I suspect that the Bind server doesn't listen to the tun0-interface only eth0, but the Bind manual says it should listen to all interfaces by default.

The server log shows:
```
named[9639]: client 10.8.0.10#3807: RFC 1918 response from Internet for 1.0.8.10.in-addr.arpa
```

How do I get these DNS queries to resolve thru the tunnel?

---

### Post by SeijiSensei on 2011-07-08
What do you have in the "listen-on" directive in named.conf?  Do you have an "allow-query" directive?  Does it specify the VPN subnet?

Does the DNS server itself have a hostname?  Do you have forward and reverse DNS configured for it?

---

### Post by niglas on 2011-07-08
> **SeijiSensei said:**
> What do you have in the "listen-on" directive in named.conf?
I did not set it since [this]("http://zytrax.com/books/dns/ch7/hkpng.html") site says ```
The default is port 53 on all server interfaces.
```> **SeijiSensei said:**
> Do you have an "allow-query" directive?  Does it specify the VPN subnet?
I did not set it since [this]("http://zytrax.com/books/dns/ch7/queries.html") site says ```
defaults to **allow-query {any;};**
```> **SeijiSensei said:**
> Does the DNS server itself have a hostname?
Yes there is a name in /etc/hostname if that is what you mean.
Otherwise, yes the DNS server is also authority of one domain.
I tried query both the the domain the server is authority for and other domains.

> **SeijiSensei said:**
> Do you have forward and reverse DNS configured for it?
Yes, a authority zone with both forward and reverse DNS, and I also kept the standard zones in the file zones.rfc1918 that includes for example:
```
zone "10.in-addr.arpa"      { type master; file "/etc/bind/db.empty"; };
```I also tried not to include that zones.rfc1918 file, but with no difference.

This is the option part of my named.conf:
```
options {
        directory "/var/cache/bind";

        allow-recursion { 10.8.0.0/24; };

        forwarders {
                208.67.222.222;
                208.67.220.220;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};
```Any clues?

---

### Post by SeijiSensei on 2011-07-08
> **niglas said:**
> I did not set it since [this]("http://zytrax.com/books/dns/ch7/hkpng.html") site says ```
The default is port 53 on all server interfaces.
```

That doesn't mean it wasn't set in named.conf by the distribution packager.  Don't rely on third-party documentation; look at the file yourself.

Many distros set very restrictive configurations for security.  As an example, mail servers like sendmail and Postfix only listen on localhost by default in Ubuntu.  I don't know what the defaults for bind9 are in Ubuntu, since I run my servers on CentOS.  

One thing you can try is installing a copy of nmap and running 

```
nmap -sU -p 53 ip.of.name.server
```

to see whether the listener is visible.  Perhaps there's a firewalling rule in place?

Obviously you'd need to run this from another machine on the network.

> Yes there is a name in /etc/hostname if that is what you mean.

No, I meant, do the zone files for the server's domain and its IP address include the DNS server itself.  If you run "host name.of.ip.server localhost" do you get the IP address in response?  What about "host -t ptr ip.addr.of.server localhost"?

---

### Post by doas777 on 2011-07-08
I wonder if the interface is up when the bind daemon starts. to test, restart named after establishing the vpn tunnel, and see if it works now.

---

### Post by niglas on 2011-07-08
Thanks for the replies!

I tried restarting bind after establishing the tunnel - no difference.

I did some successful lookups from external sites, so I don't think there's a problem with the firewall or that bind is set to deny the request. My guess is that it is something with how OpenVPN handles DNS requests.

When I have this line in my openvpn server conf...
```
 push "redirect-gateway def1 bypass-dhcp"
```...shouldn't the request go thru the tunnel even if the DNS server is not on my own network?

When I tried to push out an external DNS server the traffic doesn't seem to go thru the tunnel... Is that how it should be? It just goes thru the tunnel if the DNS server is on the tunnel interface (e g 10.8.0.9)?

---

### Post by doas777 on 2011-07-08
is there a firewall in play? udp traffic does not pass through firewalls quite teh same way that tcp traffic does.

---

### Post by niglas on 2011-07-08
SeijiSensei:
Yes, I get the ip in response in the first command and the reverse DNS (pointer record) in response for the second command.


doas777:
Well, in iptables I just executed:
```
sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```I tried adding:
```
sudo iptables -A INPUT -p udp --dport 53 -j ACCEPT
sudo iptables -A INPUT -p udp --dport 1194 -j ACCEPT
```..but the requests are already accepted.

There's nothing else set in iptables or any other front end firewall enabled.

---

### Post by SeijiSensei on 2011-07-09
If you can see the DNS server over the tunnel, you should be able to solve this problem simply by changing /etc/resolv.conf on the client. Add a line that reads "nameserver ip.of.dns.server" to the top of the list in resolv.conf.  The client's resolver will try that server first; if it's unreachable, it will try the next IP in the list.

---

### Post by niglas on 2011-07-15
I did a dump of what's happening when performing the dns queries:

External query:
```
user@server:~$ sudo tcpdump -i eth0
17:11:38.505099 IP ext.ip.of.client.4103 > ext.ip.of.server.domain: 1+ PTR? ext.rev.ip.of.server.in-addr.arpa. (46)
17:11:38.506364 IP ext.ip.of.server.domain > ext.ip.of.client.4103: 1* 1/2/2 (135)
17:11:38.512751 IP ext.ip.of.client.4104 > ext.ip.of.server.domain: 2+ A? vecka.nu. (26)
17:11:38.529278 IP ext.ip.of.server.domain > ext.ip.of.client.4104: 2 1/2/2 A 194.9.95.202 (119)
```Internal query:
```
user@server:~$ sudo tcpdump -i tun0
17:15:28.718414 IP 10.8.0.10.4113 > 10.8.0.1.domain: 1+ PTR? 1.0.8.10.in-addr.arpa. (39)
17:15:28.772216 IP 10.8.0.1.domain > 10.8.0.10.4113: 1 NXDomain 0/1/0 (116)
17:15:28.781048 IP 10.8.0.10.4114 > 10.8.0.1.domain: 2+ A? vecka.nu. (26)
17:15:28.782093 IP 10.8.0.1.domain > 10.8.0.10.4114: 2 1/2/2 A 194.9.95.202 (119)
```So it all seems fine from the server side, but the windows client gives...
> Nonexistent domain: The computer or DNS domain name does not exist....when querying thru the tunnel interface.

---

