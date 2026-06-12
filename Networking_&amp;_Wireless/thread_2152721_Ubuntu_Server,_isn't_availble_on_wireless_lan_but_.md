---
title: "Ubuntu Server, isn't availble on wireless lan but is on local and outside wan"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by jcmorse563 on 2013-06-08
Hers the deal, I'm running ubuntu server with desktop, 12.04. I have the latest Echp admin panel installed.  I have updated resolv.conf do the dynamic reads the dns servers i want, I have static ip address, i have ufw turned off. the server is behind a linksys router with wireless, i have turned off the firewall, and disabled nat. that router is behind the comcast bussness class modem, in which i have forwarded al the nessessary ports...  I can get to the address. [www.praisechapelyc.com]("http://www.praisechapelyc.com") just fine from an outside connection. I can get to it just fine from the local machine itself, but when i type in the address from a computer (all macs) from the same lan it times out.  I have included the local ip address in network config of the macs as the dns.  The mac still work on the internet so the dns server is working fine (bind) i can ping the address and it works fine.  I have the site set so you get a "forbidden" page if i just type in the ip address, and that works.  what doesn't work are any of the vhosts from the local lan from another machine on the same network.  I set the computer up at my house and was able to access just fine at the time on the local lan, but after moving the server to its home, and updating(should have never done that), and logging the outside address in ehcp as the ip, i no longer have the lan/wireless access to apache server it times out.  Like i said every thing from outside connects just fine, and everything from localhost is good.   except for that nagging error mixing ports message that i have never been succsessfull  to get rid of, with the ehcp/ubuntu combination. any help is greatly appreciated, ive been on this problem for several days now with no luck... if you need more info please just ask.. thanks.

---

### Post by jcmorse563 on 2013-06-17
bump... need help with this, this is a church site and need to be able to access it from LAN as well as Wan...    like i said works fine from outside, but times out from LAN. Will come up local.  I done a traceroute and seems to go from local dns out to comcast then hangs there. but should route only to local dns when on the same network shouldnt it.  im running ubuntu 12.04 and the newest echp console. if anyone has any ideas please post, ive been searching for about a week on this one with nodda, thanx.

---

### Post by papibe on 2013-06-17
Hi jcmorse563.

The ability to connect to a machine from your local network using its public name, or IP, is called **NAT loopback** (read about it [here]("http://opensimulator.org/wiki/NAT_Loopback_Routers")). This an advance feature and it is not supported by most consumer routers.

I would start by checking the router's documentation in the slim case it support it.

Note that you could easily access the server from inside the LAN either using its LAN short name, or its LAN IP (e.g. 192.168.1.50).

I hope that helps. Let us know how it goes.
Regards.

---

### Post by Cheesemill on 2013-06-18
There are a couple of solutions of your router doesn't provide NAT loopback.

See my post here...
[http://ubuntuforums.org/showthread.php?t=2030003&p=12151574&viewfull=1#post12151574](http://ubuntuforums.org/showthread.php?t=2030003&p=12151574&viewfull=1#post12151574)

---

### Post by jcmorse563 on 2013-06-18
thankyou. i will look at this list and check our router, i was confused because my cisco had not problems, but i think the church has a netgear, ill post ater i check.. thanks.

---

### Post by jcmorse563 on 2013-06-18
well as far as i can see the router net gear wrn 3500 does have loop back. just to be sure  i brought one that i have used in the past and swapt them out, still no go.  a little info, i am running ubuntu 12.04. with the newest echp, I run two web servers on one machine, one for tcp service to the pages listening to port 80, or *(which throws errors but should work) this is an apache2 server, the other lighttpd listening to a special port and defaulting to the echp directory, this way i am able to secure echp to only one port other than 80 and still run vhosts on 80.  I done some playing if i shut off the lighttpd has no effect other than not being able to get to web pages, and if i shut off apache sites go down no access at all. as i would expect.  If i type in the local addess from a machine on the lan i get the forbidden page, so that is working. and we are getting to the server.  i have loaded the address of the server as a dns address on the other machines on the lan. ok so i have other pages on the server that are not registared with a external nameservice provider, if i type in 192.168.1.xx/otherpage.com i get 'not found on this server.  I read that this new echp likes xnigx better so switched and tried that, had same problem.  

heres interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.30
    netmask 255.255.255.0
    gateway 192.168.1.1
    network 192.168.1.0
    broadcast 192.168.1.255
    dns-nameserver 192.168.1.30
#    dns-nameserver 10.1.10.1
#    dns-namesever 8.8.8.8

heres hosts.
127.0.0.1    localhost
127.0.1.1    pcwebserver

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
192.168.1.30 [www.byeverywordproductions.com](www.byeverywordproductions.com) byeverywordproductions.com mail.byeverywordproductions.com [www.praisechapelyc.com](www.praisechapelyc.com) praisechapelyc.com mail.praisechapelyc.com [www.jefferymorseministries.com](www.jefferymorseministries.com) jefferymorseministries.com mail.jefferymorseministries.com [www.cspp.com](www.cspp.com) cspp.com mail.cspp.com [www.roadtobethelradio.com](www.roadtobethelradio.com) roadtobethelradio.com mail.roadtobethelradio.com localhost

here is networks,,, idn way this is here. 
# symbolic names for networks, see networks(5) for more information
link-local 169.254.0.0

here is named.conf

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
include "/etc/bind/named_ehcp.conf";

if we need more just ask what you need. im stumped, it has to be something with bind i think that. but i need someone who know more then i do...lol

---

### Post by jcmorse563 on 2013-06-18
here is named.conf.options options {
directory "/var/cache/bind";

// If there is a firewall between you and nameservers you want
// to talk to, you may need to fix the firewall to allow multiple
// ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

// If your ISP provided one or more IP addresses for stable
// nameservers, you probably want to use them as forwarders.
// Uncomment the following block, and insert the addresses replacing
// the all-0's placeholder.

// forwarders {
//     0.0.0.0;
// };

//========================================================================
// If BIND logs error messages about the root key being expired,
// you will need to update your keys.  See [https://www.isc.org/bind-keys](https://www.isc.org/bind-keys)
//========================================================================
dnssec-validation auto;

auth-nxdomain no;    # conform to RFC1035
listen-on-v6 { any; };

here is named.conf.local
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

heres  named.conf.defaultzones
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

here is named_ehcp.conf
/*
domain id:9
domainname:byeverywordproductions.com
panelusername:byeverywordproductions.com
reseller:admin
aciklama-explanation:{aciklama}
*/
zone "byeverywordproductions.com" {
        type master;
        file "/etc/bind/byeverywordproductions.com";
};

/*
domain id:6
domainname:praisechapelyc.com
panelusername:praisechapelyc.com
reseller:admin
aciklama-explanation:{aciklama}
*/
zone "praisechapelyc.com" {
        type master;
        file "/etc/bind/praisechapelyc.com";
};

/*
domain id:8
domainname:jefferymorseministries.com
panelusername:jefferymorseministries.com
reseller:admin
aciklama-explanation:{aciklama}
*/
zone "jefferymorseministries.com" {
        type master;
        file "/etc/bind/jefferymorseministries.com";
};

/*
domain id:7
domainname:cspp.com
panelusername:cspp.com
reseller:admin
aciklama-explanation:{aciklama}
*/
zone "cspp.com" {
        type master;
        file "/etc/bind/cspp.com";
};

/*
domain id:10
domainname:roadtobethelradio.com
panelusername:roadtobethelradio.com
reseller:admin
aciklama-explanation:{aciklama}
*/
zone "roadtobethelradio.com" {
        type master;
        file "/etc/bind/roadtobethelradio.com";
};

here is ifconfig.
pcwebadmin@pcwebserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:7f:f6:7f:2f  
          inet addr:192.168.1.30  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:167409 errors:0 dropped:14715 overruns:0 frame:0
          TX packets:516245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20750340 (20.7 MB)  TX bytes:680117107 (680.1 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:614446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:614446 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91322796 (91.3 MB)  TX bytes:91322796 (91.3 MB)

here is resolv.conf
 Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.30
nameserver 192.168.1.1
nameserver 8.8.8.8

---

