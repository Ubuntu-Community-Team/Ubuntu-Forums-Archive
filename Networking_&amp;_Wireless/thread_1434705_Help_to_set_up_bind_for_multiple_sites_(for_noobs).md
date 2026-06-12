---
title: "Help to set up bind for multiple sites (for noobs)"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by zereshk on 2010-03-20
Hi,

As a noob in networking, I could not find any tutorial to address my issue and have had great difficulty setting up my own DNS server (one week of headache!). I tried different servers (Bind, MaraDNS, NDS) but with no success in any of them :(

Here is the problem. I have a VPS and a main domain, say mydmn.net registered by godaddy. At  godaddy, I have defined two name-servers 

ns1.mydmn.net  pointing to 1.2.3.4 (my VPS's first IP)
ns2.mydmn.net  pointing to  1.2.3.5 (my VPS's second IP)


Now, I have several other domains, say,  mycat.com, mydog.com, which are all pointed to 
ns1.mydmn.net
ns2.mydmn.net
at their registrars (different from godaddy). 

My relevant files in Bind9  are like this:

**named.conf.local:**

> 
zone "mydmn.net" {
   type master;
        file "/etc/bind/zones/mydmn.net.db";

};

zone "mycat.net" {
        type master;
        file "/etc/bind/zones/mycat.net.db";
};


zone "mydog.net" {
        type master;
        file "/etc/bind/zones/mydog.net.db";
};


zone "0.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.0.168.198.in-addr.arpa";
}

**mycat.com.db:**

> $TTL 1h
mycat.com.  IN      SOA     ns1.mydmn.net.        [EMAIL="webadmin@mydmn.net"]webadmin@mydmn.net[/EMAIL]. (
                                                        10 ;serial
                                                        3600 ;refresh
                                                        3600 ;retry
                                                        3600 ;expire
                                                        3600 ;minimum TTL
)

mycat.com. IN  NS      ns1.mydmn.net.
mycat.com. IN  MX      10      mail.mydmn.net.
mycat.com. IN  MX      20      mail.mydmn.net.

@       IN      A   0.50    192.168.0.50
www     IN      A       192.168.0.50
mail    IN      A       192.168.0.50
ns      IN      A       192.168.

**/etc/resolv.conf:**

> 
nameserver 123.123.123.123 (my VPS provider's first IP)
nameserver 123.123.123.124 (my VPS provider's second IP)

nameserver 127.0.0.1
nameserver 1.2.3.4 (my IP provided by my VPS provider

search mydmn.net

search mycat.com
search mydog.com

I have tried many different modifications and alternative but with no success. 
So your hints or suggestions are really appreciated.

---

### Post by zereshk on 2010-03-20
Ok, I  could resolve the issue.  However these may not be the best config, or have some faults, but working so let's put here my working configurations in case it will be useful for others: (Based on fictitious domains and IPs mentioned above):


/etc/bind/named.conf.local

> zone "mydmn.net" {
   type master;
        file "/etc/bind/zones/mydmn.net.db";

};

zone "mycat.com" {
        type master;
        file "/etc/bind/zones/mycat.com.db";
};



;... the rest of zones come here


zone "1.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};
**/etc/bind/zones/mycat.com.db :**
> $TTL 1h
mycat.com.  IN      SOA     ns.mydmn.net.        [EMAIL="webadmin@mydmn.net"]webadmin@mydmn.net[/EMAIL]. (
                                                        10 ;serial
                                                        3600 ;refresh
                                                        3600 ;retry
                                                        3600 ;expire
                                                        3600 ;minimum TTL
)

mycat.com. IN  NS      ns.mydmn.net.
mycat.com. IN  MX      10      mail.mydmn.net.
mycat.com. IN  MX      20      mail.mydmn.net.

@       IN      A       1.2.3.4
www     IN      A       1.2.3.4
mail    IN      A       1.2.3.4
ns      IN      A       1.2.3.4

**/etc/resolv.conf :**

> search mydmn.net
search mycat.com

nameserver 123.123.123.123
nameserver 123.123.123.124

Please let me know if I can somehow improve these.

---

### Post by kf7ldr on 2013-01-06
I am attempting to setup a Windows Web-Server with multiple sites running off it.  I am using Ubuntu Server 12.04 with Bind 9 for DNS.  My site kf7ldr.com is setup up with GoDaddy as well as 2 other sites 111.com and 222.com.  Ubunu Server is setup as my nameserver ns1.kf7ldr.com.

Documentation I found states that I need to do the following on the Windows Server to have multiple sites:
Webserver - IIS - Server - Sites -

kf7ldr - bindings - type: http, host name: kf7ldr.com, port 80, ipaddress: 123.456.789.012

111 - bindings - type: http, host name: 111.com, port 81, ipaddress: 123.456.789.012

222 - bindings - type: http, host name: 222.com, port 82, ipaddress: 123.456.789.012

------
I am trying to get ubuntu server to recognize the ports.  Right now I just have kf7ldr.com programmed.  I will get the aliases for the other sites programmed in once i can get kf7ldr.com to function.

---
I do have a static IP from my ISP and I programmed my firewall to transfer any DNS requests to my ubuntu server.


Thanks ahead of time for any assistance in this.

---

