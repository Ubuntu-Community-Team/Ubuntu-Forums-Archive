---
title: "DNS with Bind9"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by nethompson on 2011-09-25
I am having trouble fully setting up DNS. I have my modem, my server, my router, then my personal computers. I can connect to the Internet and connect to my server via IP address. What I would like to do is access my server using its fully qualified domain name from behind my router. I have tried various things in the zone files of bind with no success. I have also searched the web for the answer. Hopefully the experts in these forums can help me.

---

### Post by Doug S on 2011-09-26
I think maybe there hasn't been a reply yet because we need more infomation to be able to supply useful suggestions. From your description, it sounds as if your server is on a seperate WAN IP address than your router. Is that correct? Or does your server have two network interface cards and your router is on the LAN side of your server? Do you have static WAN IP addreses from your ISP or do you have dynamic WAN IP addresses?

---

### Post by nethompson on 2011-09-26
Ah, my apologies. My server has two NICs. The first NIC has the IP address in the 192.168.1.0 network. My second NIC has the IP address in the 192.168.0.0 network which supplies my router an IP address in that same network and also provides DNS. My router then supplies dynamic IP addresses to all other devices in the 192.168.2.0 network.

---

### Post by Kelketek on 2011-09-26
Can you post your zone file here? I'm assuming you've already set up your private name servers at your registrar and pointed them at two separate Internet-facing IP addresses on your server, correct? What's the domain name?

And, perhaps more importantly, is this your home network or a business account on a T1/business cable, etc? How many public IPs do you have?

---

### Post by Doug S on 2011-09-27
I agree with Kelketek that we need to see your zone file, and I should have thought of that in my first posting. If you are just trying to supply intranet DNS stuff, then, with all due respect, I don't agree with the rest of what Kelketek says. I don't know if it will help or confuse things, but I will post a portion of my zone file below:
> ;
; BIND data file for smythies.com
;
$TTL 604800
@ IN SOA smythies.com. doug.smythies.com. (
2011042900 ; Serial
604800 ; Refresh
86400 ; Retry
2419200 ; Expire
604800 ) ; Negative Cache TTL
IN A 192.168.111.1
;
@ IN NS ns1.smythies.com.
ns1 IN A 192.168.111.1
www IN A 192.168.111.1
DOUG-64 IN CNAME ns1
bla IN CNAME ns1
mail IN CNAME ns1
Wireless-R IN A 192.168.111.57
... etc... for other intranet devices...
Of course, I also have my DHCP server (it would be your router in your case) set to give 192.168.111.1 as the first namer server.

---

### Post by Kelketek on 2011-09-27
Ah, I misread his original post as wanting to access his servers from beyond his router rather than behind it.

You should indeed set the name server as your first name server in DHCP. You should /also/ put 127.0.0.1 in /etc/resolv.conf of your DNS server, as well as the IP addresses of your ISP's name servers under that.

This makes sure that when your server looks up a name, it always checks itself first-- which is important when doing intranet name servers, since if you don't have a public configuration for those names, you may have some trouble (and outside IP addresses would be different anyway).

You should probably make sure the name server is also set to do recursive queries. You may have some trouble (or delays) in DNS resolution for outside IP addresses otherwise, since your computers will be configured by DHCP to check the name server first.

---

### Post by nethompson on 2011-09-27
It seems like I am being misunderstood and thats my fault for not being completely clear. What I am ultimately trying to do is access my server from my personal device(s) which are behind the router. I am currently having to access my server using its IP address of 192.168.0.1 and I would like to use its name instead. I can already connect to my server from outside my network using its FQDN.

---

### Post by Doug S on 2011-09-27
Yes, I understand, and that is very similar to my network. Everything Kelketek and I said, at least after we eliminated our misunderstandings, applies. While I posted a portion of my own db.smythies.com file, it is only one of several files. Also things look different from the outside world. It still isn't clear to me where your troubles are, so I cann't yet supply more specific suggestions. However, below is output from an nslookup on one of my windows computers, where you can see it used my server as the DNS server:> 
C:\Users\Doug\SPlot\scripts>nslookup ubuntu.org
Server: ns1.smythies.com
Address: 192.168.111.1
Non-authoritative answer:
Name: ubuntu.org
Address: 147.83.195.55

Edit: below are, perhaps, more relevant examples:>  
C:\Users\Doug>nslookup bla.smythies.com
Server: ns1.smythies.com
Address: 192.168.111.1
Name: ns1.smythies.com
Address: 192.168.111.1
Aliases: bla.smythies.com
 
C:\Users\Doug>nslookup smythies.com
Server: ns1.smythies.com
Address: 192.168.111.1
Name: smythies.com
Address: 192.168.111.1
 
C:\Users\Doug>nslookup [www.smythies.com]("http://www.smythies.com")
Server: ns1.smythies.com
Address: 192.168.111.1
Name: [www.smythies.com]("http://www.smythies.com")
Address: 192.168.111.1

And and example lookup from the server itself:>  
doug@doug-64:$ nslookup bla.smythies.com
Server: 127.0.0.1
Address: 127.0.0.1#53
bla.smythies.com canonical name = ns1.smythies.com.
Name: ns1.smythies.com
Address: 192.168.111.1


---

### Post by nethompson on 2011-09-27
Here is my zone file, my reverse lookup file, and my named configuration file. I am still fairly new at this as you can tell and I appreciate your efforts to help me understand this.

**[SIZE=2]Zone:[/SIZE]**

$TTL 3D
digitalsecurity-ga.local.     IN SOA  server.digitalsecurity-ga.local. admin.digitalsecurity-ga.local. (

2011091702      ; serial
28800           ; refresh
3600            ; retry
604800          ; expire
38400           ; min
)

digitalsecurity-ga.local    IN    NS          server.digitalsecurity-ga.local.
www                IN      CNAME        server.digitalsecurity-ga.local //an example
server                IN      A        192.168.1.2 //an example
gw                IN      A        192.168.1.1   //an example


[SIZE=2]**Reverse lookup Zone:**[/SIZE]

$TTL 3D

1.168.192.IN-ADDR.ARPA IN SOA server.digitalsecurity-ga.local. admin.digitalsecurity-ga.local. (
                                2011091902 ; serial
                                28800      ; refresh (8 hours)
                                7200       ; retry (2 hours)
                                604800     ; expire (1 week)
                                86400      ; minimum (1 day)
                                )
    
    IN    NS    server.digitalsecurity-ga.local.
1    IN    PTR     digitalsecurity-ga.local.


[SIZE=2]**named.conf:**[/SIZE]

zone "." {
        type hint;
        file "/etc/bind/db.root";
};

zone "digitalsecurity-ga.local" { //change asus.local to whatever you named your domain such as mydomain.local
type master;
file "/etc/bind/zones/digitalsecurity-ga.local.db"; //this file or foler does not exist so we will need to make it
};
zone "1.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";//this file does not exist so we will also need to make it
};
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

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
 
 controls {
     inet 127.0.0.1 port 953
         allow { 127.0.0.1; } keys { "rndc-key"; };
 };
# End of named.conf

---

### Post by Doug S on 2011-09-28
My suggestions for the first two files are:
>  
Zone:
 
$TTL 3D
@ IN SOA digitalsecurity-ga.local. admin.digitalsecurity-ga.local. (
2011091702 ; serial
28800 ; refresh
3600 ; retry
604800 ; expire
38400 ; min
)
@ IN NS server.digitalsecurity-ga.local.
server IN A 192.168.1.2
www IN A 192.168.1.2
gw IN A 192.168.1.1
 
Reverse lookup Zone:
 
$TTL 3D
@ IN SOA server.digitalsecurity-ga.local. admin.digitalsecurity-ga.local. (
2011091902 ; serial
28800 ; refresh (8 hours)
7200 ; retry (2 hours)
604800 ; expire (1 week)
86400 ; minimum (1 day)
)
@ IN NS server.digitalsecurity-ga.local.
1 IN PTR gw.digitalsecurity-ga.local.
2 IN PTR server.digitalsecurity-ga.local.

You need to use an A record for www not a CNAME.
Typically (I think), local named stuff is done in named.conf.local instead of named.conf. I don;t know about the controls part.
What is in your /etc/resolv.conf file? Even if it isn't working properly yet, are your devices trying to use your server for DNS lookups? i.e. like the examples I showed in my previous post?

---

### Post by nethompson on 2011-09-28
Ok, here are my updated files to what I understand. I don't know if this is right but for some reason I just don't seem to understand where I'm going wrong here.

digitalsecurity-ga.com.db:

$TTL 3D

[www.digitalsecurity-ga.com]("http://www.digitalsecurity-ga.com")    IN    SOA    ns1.digitalsecurity-ga.com. admin.digitalsecurity-ga.com. (

                                2008110601 ; serial
                                28800      ; refresh (8 hours)
                                7200       ; retry (2 hours)
                                604800     ; expire (1 week)
                                86400      ; minimum (1 day)
                                )

[www.digitalsecurity-ga.com]("http://www.digitalsecurity-ga.com")    IN    A local IP
local IP.in-addr.arpa.    IN    PTR    digitalsecurity-ga.com.
digitalsecurity-ga.com        IN    NS    ns1.digitalsecurity-ga.com.
[www.digitalsecurity-ga.com]("http://www.digitalsecurity-ga.com")    IN    CNAME    digitalsecurity-ga.com.
ftp.digitalsecurity-ga.com    IN    CNAME    digitalsecurity-ga.com.


rev.0.168.192.in-addr.arpa:

$TTL 3D

@            IN    SOA    ns1.digitalsecurity-ga.com. admin.digitalsecurity-ga.com. (

                                2011091902 ; serial
                                28800      ; refresh (8 hours)
                                7200       ; retry (2 hours)
                                604800     ; expire (1 week)
                                86400      ; minimum (1 day)
                                )

@            IN    NS    ns1.digitalsecurity-ga.com.
1            IN    PTR    ns1.digitalsecurity-ga.com.
2            IN    PTR    gw.digitalsecurity-ga.com.

rev.1.168.192.in-addr.arpa:

$TTL 3D

@            IN    SOA    server.digitalsecurity-ga.com. admin.digitalsecurity-ga.com. (

                                2011091902 ; serial
                                28800      ; refresh (8 hours)
                                7200       ; retry (2 hours)
                                604800     ; expire (1 week)
                                86400      ; minimum (1 day)
                                )

@            IN    NS    ns1.digitalsecurity-ga.com.
1            IN    PTR    server.digitalsecurity-ga.com.
2            IN    PTR    gw.digitalsecurity-ga.com.

---

### Post by Doug S on 2011-09-29
I am not sure how to help you. We need more information such as what errors are you getting? What are some log file entries? What is in your /etc/resolv.conf file? Are the devices on your local network pointing to your server DNS as the first place to look? ...
Delete the rev.1.168.192.in-addr.arpa file, as you are not providing DNS is that direction. Sorry, I missed that the other day. From your description you are only providing DNS on your 192.168.0.XXX LAN.
I still suggest that your digitalsecurity-ga.com.db should look more like the example I gave, rather than what you have.
For references I have been using the [Ubuntu server guide ]("https://help.ubuntu.com/10.10/serverguide/C/index.html")([PDF]("https://help.ubuntu.com/10.10/serverguide/C/serverguide.pdf"))and the other references it lists in the DNS section.

---

### Post by nethompson on 2011-09-29
I finally got it! Thanks for all of your help everyone. The biggest issue that I was having was understanding the different records and how to use them. I found a really good explanation which allowed me to configure everything the way I want it. Thank you to everyone who assisted me with this.

---

