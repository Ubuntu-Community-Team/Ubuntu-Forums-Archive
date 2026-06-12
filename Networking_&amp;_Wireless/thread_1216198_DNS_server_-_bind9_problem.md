---
title: "DNS server - bind9 problem"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by mthalis on 2009-07-18
I had two servers one for auth server and other for gateway my auth server has web server. I have local network local network client should access web server using name instead of ip adrress([http://ites-desktop.lk/](http://ites-desktop.lk/))

My gateway server have dhcp server it issue ip to client In order to clients access web server using name i set up dns server in gateway machine. Below shows my configuration

auth server 192.168.20.253
gateway server -- 192.168.101.232 - go Internet
                  192.168.20.254  - local network(issue dhcp) 
client range  --- 192.168.20.1 to 192.168.20.20
Default Dns serve -- 203.115.0.18



[B]
dhcpd.conf[/B]
```
ddns-update-style interim;


subnet 192.168.20.0 netmask 255.255.255.0 {
 #       option routers                  192.168.101.1;
	 option routers			 192.168.20.254;  
         option subnet-mask              255.255.255.0;

         option domain-name              "ites-desktop.lk";
	 #option domain-name              "192.168.20.253";
         option domain-name-servers       192.168.20.254,203.115.0.18;
	 #option domain-name-servers       192.115.0.18;

        #option time-offset              -18000;     # Eastern Standard Time

#	range 192.168.20.1 192.168.20.254
	range dynamic-bootp 192.168.20.1 192.168.20.24;
        }
```


[B]
named.conf.local[/B]
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

// This is the zone definition. replace example.com with your domain name
zone "ites-desktop.lk" {
        type master;
        //file "/etc/bind/zones/ites-desktop.lk.db";
	file "/etc/bind/zones/ites-desktop.lk.zone";
        };

// This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "20.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.20.168.192.in-addr.arpa";
};


```

**named.conf.options**

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
	 	203.115.0.18;
	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

```

**ites-desktop.lk.zone**
```

//gateway.itess.lk - DNS server Name(I got it from /etc/hosts file)
ites-desktop.lk. IN      SOA     gateway.itess.lk.ites-desktop.lk. admin.ites-desktop.lk. (
          2006071801 
          28800       
          3600        
          604800    
          38400 )    
ites-desktop.lk. IN      NS      gateway.itess.lk.ites-desktop.lk.
ites-desktop.lk. IN      MX     10 mta.ites-desktop.lk.

www           IN      A       192.168.20.253
mta              IN      A       192.168.20.253
gateway.itess.lk               IN       A        192.168.20.254


```

**www ** please clarify this worlds.  

**rev.20.168.192.in-addr.arpa**
```
//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
//gateway.itess.lk - DNS server Name(I got it from /etc/hosts file)
//Ip address 192.168.20.254
@ IN SOA ns1.ites-desktop.lk. admin.ites-desktop.lk. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                     IN    NS     gateway.itess.lk.ites-desktop.lk.
254                    IN    PTR    ites-desktop.lk

```

**resolv.conf**
```
#search itess.lk,ites-desktop.lk
#nameserver 203.115.0.1,192.168.20.254

search ites-desktop.lk
nameserver 192.168.20.254

```

**host**
```
127.0.0.1	localhost
192.168.101.232	gateway.itess.lk	gateway
#192.168.20.253 ites-desktop.lk
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

if i type **dig ites-desktop.lk** gave
```
; <<>> DiG 9.5.1-P2 <<>> ites-desktop.lk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 24419
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;ites-desktop.lk.		IN	A

;; AUTHORITY SECTION:
ites-desktop.lk.	38400	IN	SOA	ns1.ites-desktop.lk. admin.ites-desktop.lk. 2006071801 28800 3600 604800 38400

;; Query time: 0 msec
;; SERVER: 192.168.20.254#53(192.168.20.254)
;; WHEN: Sat Jul 18 11:08:07 2009
;; MSG SIZE  rcvd: 79

```

if I type **nslookup ites-dektop.lk** below error happen
```
Server:		192.168.20.254
Address:	192.168.20.254#53

** server can't find ites-dektop.lk: NXDOMAIN

```

I did this in windows but gave same error.

How can I fix it, I don't have excellent idea about networking. Please help me I'm waiting you're comments.

---

### Post by mthalis on 2009-07-19
Any suggestion?

---

### Post by mthalis on 2009-07-20
Below show my new configuration

**dhcp.conf**
```

subnet 192.168.20.0 netmask 255.255.255.0 {
 #       option routers                  192.168.101.1;
	 option routers			 192.168.20.254;  
         option subnet-mask              255.255.255.0;

         option domain-name              "www.ites-desktop.lk";
	 #option domain-name              "192.168.20.253";
         option domain-name-servers       192.168.20.254,203.115.0.18;
	 #option domain-name-servers       192.115.0.18;

        #option time-offset              -18000;     # Eastern Standard Time

#	range 192.168.20.1 192.168.20.254
	range dynamic-bootp 192.168.20.1 192.168.20.24;
        }

```
[B]
named.conf.local[/B]

```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

// This is the zone definition. replace example.com with your domain name
zone "ites-desktop.lk" {
        type master;
        file "/etc/bind/zones/ites-desktop.lk.db";
	//file "/etc/bind/zones/ites-desktop.lk.zone";
        };

// This is the zone definition for reverse DNS. replace 0.168.192 with your network address in reverse notation - e.g my network address is 192.168.0
zone "20.168.192.in-addr.arpa" {
     type master;
     file "/etc/bind/zones/rev.20.168.192.in-addr.arpa";
};


```
[B]
named.conf.options[/B]

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
	 	203.115.0.18;
	 };

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};


```

**ites-desktop.lk.db**

```

ites-desktop.lk.   IN      SOA     gateway.ites-desktop.lk. admin.ites-desktop.lk. (
	 2006081401
         28800
         3600
         604800
         38400) 
ites-desktop.lk.   IN      NS              gateway.ites-desktop.lk.
ites-desktop.lk.   IN      MX     10       mta.ites-desktop.lk.
www                IN      A       192.168.20.253
mta                IN      A       192.168.101.100
gateway            IN      A       192.168.20.254





```


**rev.20.168.192.in-addr.arpa**

```

//replace example.com with yoour domain name, ns1 with your DNS server name.
// The number before IN PTR example.com is the machine address of the DNS server. in my case, it's 1, as my IP address is 192.168.0.1.
@ IN SOA     gateway.ites-desktop.lk. admin.ites-desktop.lk. (
                        2006081401;
                        28800; 
                        604800;
                        604800;
                        86400 
)

                       IN    NS     gateway.ites-desktop.lk.
254                    IN    PTR    ites-desktop.lk

```

**resolv.conf**

```

#search itess.lk,ites-desktop.lk
#nameserver 203.115.0.1,192.168.20.254

search www.ites-desktop.lk
#nameserver 192.168.20.254
nameserver 127.0.0.1

```

**host**

```

127.0.0.1	localhost
192.168.101.232	gateway.itess.lk	gateway
#192.168.20.253 ites-desktop.lk
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

if i type dig [www.ites-desktop.lk](www.ites-desktop.lk) gave

```


; <<>> DiG 9.5.1-P2 <<>> www.ites-desktop.lk
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38744
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;www.ites-desktop.lk.		IN	A

;; ANSWER SECTION:
www.ites-desktop.lk.	38400	IN	A	192.168.20.253

;; AUTHORITY SECTION:
ites-desktop.lk.	38400	IN	NS	gateway.ites-desktop.lk.

;; ADDITIONAL SECTION:
gateway.ites-desktop.lk. 38400	IN	A	192.168.20.254

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Jul 20 12:26:01 2009
;; MSG SIZE  rcvd: 91


```

if I type **nslookup [www.ites-desktop.lk](www.ites-desktop.lk)** in Ubuntu server

```

Server:		127.0.0.1
Address:	127.0.0.1#53

Name:	www.ites-desktop.lk
Address: 192.168.20.253


```

Ubuntu client 

```


Server:		192.168.20.254
Address:	192.168.20.254#53

Name:	www.ites-desktop.lk
Address: 192.168.20.253

```

But windows give below error 

```

Can't find server name for address 192.168.20.254:server fail

```

How can i fix it(I type this command several windows xp machines above error happen)..

Please give you're comments.

---

### Post by mthalis on 2009-07-20
After several hours later windows also work greatly.
New problem is after restarting bind9 server issue below error

```

Stopping domain name service... bind9                                        rndc: connection to remote host closed
This may indicate that
* the remote server is using an older version of the command protocol,
* this host is not authorized to connect,
* the clocks are not syncronized, or
* the key is invalid.
                                                                  [ OK ]
 * Starting domain name service... bind9                          [ OK ]

```

How can I fix it.

---

### Post by mthalis on 2009-07-21
After restating machine everything work fine, I don't know what exactly happen can any clarify it.

---

