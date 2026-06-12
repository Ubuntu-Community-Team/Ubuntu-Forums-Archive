---
title: "Anybody good with bind?"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by wsonar on 2009-05-14
so I wasn't able to dig or nslookup and of my locals pc's so I decided to try to get my dns server configured I followed this how to here.

[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html]("http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html")

but somehow am missing something

when I try to restart bind it fails to start 

here's my daemon.log

```
May 14 08:07:40 oasis named[3038]: received control channel command 'stop -p'
May 14 08:07:40 oasis named[3038]: shutting down: flushing changes
May 14 08:07:40 oasis named[3038]: stopping command channel on 127.0.0.1#953
May 14 08:07:40 oasis named[3038]: stopping command channel on ::1#953
May 14 08:07:40 oasis named[3038]: no longer listening on ::#53
May 14 08:07:40 oasis named[3038]: no longer listening on 127.0.0.1#53
May 14 08:07:40 oasis named[3038]: no longer listening on 192.168.1.100#53
May 14 08:07:40 oasis named[3038]: exiting
May 14 08:07:40 oasis named[13175]: starting BIND 9.5.1-P2 -u bind
May 14 08:07:40 oasis named[13175]: found 1 CPU, using 1 worker thread
May 14 08:07:40 oasis named[13175]: using up to 4096 sockets
May 14 08:07:40 oasis named[13175]: loading configuration from '/etc/bind/named.conf'
May 14 08:07:40 oasis named[13175]: /etc/bind/named.conf.local:15: expected quoted string near '&#8220;'
May 14 08:07:40 oasis named[13175]: loading configuration: unexpected token
May 14 08:07:40 oasis named[13175]: exiting (due to fatal error)
May 14 08:15:35 oasis named[13382]: starting BIND 9.5.1-P2 -u bind
May 14 08:15:35 oasis named[13382]: found 1 CPU, using 1 worker thread
May 14 08:15:35 oasis named[13382]: using up to 4096 sockets
May 14 08:15:35 oasis named[13382]: loading configuration from '/etc/bind/named.conf'
May 14 08:15:35 oasis named[13382]: /etc/bind/named.conf.local:15: expected quoted string near '&#8220;'
May 14 08:15:35 oasis named[13382]: loading configuration: unexpected token
May 14 08:15:35 oasis named[13382]: exiting (due to fatal error)

```

here is the named.conf.local

```
 
# This is the zone definition. replace example.com with your domain name

zone &#8220;ossnet.org&#8221; {
type master;
file &#8220;/etc/bind/zones/ossnet.org.db&#8221;;
};

# This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notati$

zone &#8220;1.168.192.in-addr.arpa&#8221; {
type master;
file &#8220;/etc/bind/zones/rev.1.168.192.in-addr.arpa&#8221;;
};


```
I'm a little confused on the network address in the above file my router is set to the 192.168.1.1 and my main server is using .100



Here is the named.conf file

```

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";

```

and here's the named .conf.options file

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

 forwarders {
        68.87.5.98;   
        68.87.69.146;

 };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```


I have this zone file I created maybe it's the problem ?
rev.1.168.192.in-addr.arp

```
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it&#8217;s 1, as my $
@ IN SOA ns1.example.com. admin.example.com. (
2007031001;
28800;
604800;
604800;
86400
)

IN NS oasis.ossnet.org.
1 IN PTR ossnet.org


```

I a little confused on this also
("The number before IN PTR example.com is the machine address of the DNS server. in my case, it&#8217;s 1,")

what do they mean here? here that the last octet of the server IP?


Any help greatly appreciated

---

### Post by dandnsmith on 2009-05-14
If your server is 192.168.1.100
then the last octet (here, 8 bits) will be 100

---

### Post by wsonar on 2009-05-14
> **dandnsmith said:**
> If your server is 192.168.1.100
then the last octet (here, 8 bits) will be 100

ok cool kinda thought that may be it.

---

### Post by wsonar on 2009-05-14
I corrected the file but still get this

```
May 14 10:23:41 oasis named[15479]: starting BIND 9.5.1-P2 -u bind
May 14 10:23:41 oasis named[15479]: found 1 CPU, using 1 worker thread
May 14 10:23:41 oasis named[15479]: using up to 4096 sockets
May 14 10:23:41 oasis named[15479]: loading configuration from '/etc/bind/named$
May 14 10:23:41 oasis named[15479]: /etc/bind/named.conf.local:15: expected quo$
May 14 10:23:41 oasis named[15479]: loading configuration: unexpected token
May 14 10:23:41 oasis named[15479]: exiting (due to fatal error)
```

---

### Post by wsonar on 2009-05-14
I corrected this file and may be progressing 

```
// Also, replace ns1 with the name of your DNS server
ossnet.org. IN SOA oasis.ossnet.org. admin.ossnet.org. (
// Do not modify the following lines!
2007031001
28800
3600
604800
38400
)


// Replace the following line as necessary:
ns1 = oasis.ossnet.org
mail = oasis.ossnet.org
ossnet.org = domain name
ossnet.org. IN NS oasis.ossnet.org.
ossnet.org. IN MX 10 oasis.ossnet.org.

// Replace the IP address with the right IP addresses.
www IN A 192.168.1.100
mta IN A 192.168.1.100
ns1 IN A 192.168.1.100

```

this is what I get when I try to do a nslookup

```
devwray@oasis:/etc/bind/zones$ nslookup 192.168.1.10
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find 10.1.168.192.in-addr.arpa.: NXDOMAIN

```

---

### Post by wsonar on 2009-05-14
devwray@oasis:/var/log$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                                                                 rndc: connect failed: 127.0.0.1#953: connection refused
                                                                                                                  [ OK ]
 * Starting domain name service... bind9                                                                          [fail]

---

### Post by wsonar on 2009-05-14
Still show same error

```
May 14 10:45:49 oasis named[16242]: starting BIND 9.5.1-P2 -u bind
May 14 10:45:49 oasis named[16242]: found 1 CPU, using 1 worker thread
May 14 10:45:49 oasis named[16242]: using up to 4096 sockets
May 14 10:45:49 oasis named[16242]: loading configuration from '/etc/bind/named.conf'
May 14 10:45:49 oasis named[16242]: /etc/bind/named.conf.local:15: expected quoted string near '“'
May 14 10:45:49 oasis named[16242]: loading configuration: unexpected token
May 14 10:45:49 oasis named[16242]: exiting (due to fatal error)
```

---

### Post by wsonar on 2009-05-14
Seems like it is  querying the router instead of the server

---

### Post by puppywhacker on 2009-05-14
I prefer dig over nslookup.
when you did the NS lookup it shows that it is looking at server 192.168.1.1
That is because that is the default nameserver in /etc/resolv.conf

```
dig @localhost www
```

Your bind server doesn't start because ther is an error in your named.conf. On line 15 or before it complains about the quotes. Be aware that an ” is a different from " although they look the same, they have different meanings. It's the last quote that you want, not the cursive one.

```
loading configuration from '/etc/bind/named.conf'
/etc/bind/named.conf.local:15: expected quoted string near '“'

```

you posted an attempt to do a reversed lookup where you try to find the name of an ip-address, but that should be specified in bind in a different zone file. You can again use dig to do the reverse lookup

```
dig -x @localhost 192.168.1.100
```

---

### Post by wsonar on 2009-05-14
I guess since I copied some from the how to it put the cursive quotes in there

---

### Post by wsonar on 2009-05-14
Thanks for the help

the bind daemon starts now but I'm still not able to do a reverse lookup and get one of my local computer name's from IP which is my main goal

here is my resolv.conf

```

nameserver ossnet.org
nameserver oasis.ossnet.org
nameserver 192.168.1.1


```

---

### Post by uupreti on 2009-05-14
> **wsonar said:**
> Thanks for the help

the bind daemon starts now but I'm still not able to do a reverse lookup and get one of my local computer name's from IP which is my main goal

here is my resolv.conf

```

nameserver ossnet.org
nameserver oasis.ossnet.org
nameserver 192.168.1.1


```

Try following in /etc/resolv.conf instead
nameserver xx.xx.xx.xx (ip address of dns server itself or localhost and remove all lines)

If connection is refused then try to reload rndc service by **rndc reload**

---

### Post by wsonar on 2009-05-14
I tried with

nameserver localhost    

```
devwray@oasis:~$ nslookup 192.168.1.10
;; Got SERVFAIL reply from 127.0.0.1, trying next server
;; Got SERVFAIL reply from 127.0.0.1, trying next server
Server:		::1
Address:	::1#53

** server can't find 10.1.168.192.in-addr.arpa: SERVFAIL

```

nameserver 192.168.1.100 
```
devwray@oasis:~$ nslookup 192.168.1.10
Server:		192.168.1.100
Address:	192.168.1.100#53

** server can't find 10.1.168.192.in-addr.arpa: SERVFAIL

```

and with the router in the resolv.conf
```
devwray@oasis:~$ sudo nano /etc/resolv.conf
devwray@oasis:~$ sudo /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                                                          [ OK ] 
 * Starting domain name service... bind9                                                                          [ OK ] 
devwray@oasis:~$ nslookup 192.168.1.10
Server:		192.168.1.1
Address:	192.168.1.1#53

** server can't find 10.1.168.192.in-addr.arpa.: NXDOMAIN

```
........................................................

I have a netgear router I use for DHCP
I use easydns so the world can see my (Web and email)
I want to use my ubuntu server as a local Name server(so I can queary my local box's)

I have one server for now it has my mail/web/DNS

I'm using nslookup just because I  don't need all that info I just want the host name from the IP

---

### Post by wsonar on 2009-05-14
I guess the problem might be my machine's are DHCP so they are not getting the ubuntu server as the DNS server

---

### Post by wsonar on 2009-05-14
I think I need to add the ubuntu server as a dns server on my router

guess I will test that when I get home, Got a feeling that will do it

haven't setup remote management on the router yet

---

### Post by uupreti on 2009-05-14
> **wsonar said:**
> I guess the problem might be my machine's are DHCP so they are not getting the ubuntu server as the DNS server

I wonder your bind is running properly. Can you give output of following commands.

1. **ps aux | grep bind**
2. **dig -x 192.168.1.10 @localhost** (or ip of dns server)

---

### Post by wsonar on 2009-05-14
```
devwray@oasis:~$ ps aux | grep bind
root      3830  0.0  0.0  10600  1748 ?        Ss   May06   0:00 /usr/sbin/winbindd
root      3838  0.0  0.0  10600  1196 ?        S    May06   0:00 /usr/sbin/winbindd
bind     19348  0.0  0.4  41536  8368 ?        Ssl  13:49   0:00 /usr/sbin/named -u bind
devwray  19888  0.0  0.0   3340   804 pts/0    S+   14:27   0:00 grep bind


devwray@oasis:~$ dig -x 192.168.1.10 @localhost

; <<>> DiG 9.5.1-P2 <<>> -x 192.168.1.10 @localhost
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 2690
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;10.1.168.192.in-addr.arpa.	IN	PTR

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Thu May 14 14:34:56 2009
;; MSG SIZE  rcvd: 43


```

---

### Post by wsonar on 2009-05-14
So I tried adding my ubuntu server to my Netgear router as a DNS server, but am still not having any luck

my results are still the same

---

### Post by uupreti on 2009-05-14
Try hosting this ip to your local domain and try to dig hostname. 

For example lets say [www.abc.com](www.abc.com) will be assigned to 192.168.1.10 ip. for now try to avoid all reverse zone settings in named.conf file.

Try **dig [www.abc.com](www.abc.com)**. Let's see what will be the result.

---

### Post by wsonar on 2009-05-14
from the server I can  only get a response from a dig localhost or external addresses like yahoo or google

If I try to dig my mail or web server I cannot dig them from the server, but I can dig them from my other workstation

---

### Post by helgman on 2009-05-15
I had some trouble setting up BIND on Ubuntu this weekend and what I learned what that "you can't fool the system". The good things are ...

There are a few good tools like namedcheck-xxx (not sure about that exact names) that will let you check your configuration and zone-files to make sure that they area correct.

The second thing that finaly made my machine fly was changing the directory where I stored my zone-files. I changed the "directory" to something other then /var/cache/bind (or maybe I rather stated (in the configuration for the zone) that: file "/some/folder/some/where/oh/here/is/the/file";) - setting the directory to default (/var/cache/bind) and then putting the files there (and pointing to them when defining the zones) did the trick (as I recall).

I'll take a look when I get home (today or tomorrow) if your problem hasn't been solved by then ...

Regards,
Helgman

---

### Post by helgman on 2009-05-17
Sample config from /etc/bind/named.conf.local:
```
zone "example.com" {
	type master;
	file "example.com";
};
```
Sample zone-file (example.com) in /var/cache/bind/:
```
$ORIGIN example.com.
$TTL 86400
@		IN	SOA	example.com.	hostmaster.example.com. (
		2009050801	; serial
		21600		; refresh after 6 hours
		3600		; retry after 1 hour
		604800		; expire after 1 week
		86400 )		; minimum TTL of 1 day

		IN	NS	example.com.

host1	IN	A	192.168.1.1
host2	IN	A	192.168.1.2
host3	IN	A	192.168.1.3
```

It is also possible to check the config with ```
named-checkconf
``` and the zone files with ```
named-checkzone *example.com* */var/cache/bind/example.com*
``` to look for potential problems.

I've not had any luck with changing the directory in /etc/bind/named.conf.options and that one points to /var/cache/bind - so a good way to start might be to put the zone files in there and make sure that everything works.

Regards,
Helgman

---

### Post by wsonar on 2009-05-18
Cool I'll investigate this more tonight..

thanks

---

### Post by uupreti on 2009-05-20
Yeah it is always good to check your zone file and conf file using this tool before starting or restarting bind service. Something since quote will make you crazy for a whole day.

Thanks **helgman** for remind this tool for us.

---

