---
title: "Bind9 configuration - failed to start - dns/ddns"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by linubu on 2011-12-31
Hi. 
I'm trying to set dns and ddns service on my linux box with 10.10 ubuntu.

**This is what i have:**
- static ip address 85.113.xx.xx
- local ip's from 192.168.1.50 - 200
- installed bind 9
- installed dhcp3
- installed gadmin-bind tool

My goal is to offer "free" dns and ddns service for our costumers.
I'ts not much. It's around 40 users. 
--------------------------------------------------------------------------------
[B]Problems:
[/B]When i restart bind service i get this error.
                     p { margin-bottom: 0.08in; }  [SIZE=2]* Stopping domain name service... bind9                                                                                                                                                        rndc: connection to remote host closed                                                                                                                                                          [/SIZE] 
 [SIZE=2]This may indicate that                                                                                                                                                                          [/SIZE] 
 [SIZE=2]* the remote server is using an older version of the command protocol,                                                                                                                          [/SIZE] 
 [SIZE=2]* this host is not authorized to connect,[/SIZE]
 [SIZE=2]* the clocks are not synchronized, or[/SIZE]
 [SIZE=2]* the key is invalid.            [ OK ][/SIZE]
  [SIZE=2]* Starting domain name service... bind9 [/SIZE][SIZE=2][ fail ][/SIZE] 
 
> This is my named.conf:
                     p { margin-bottom: 0.08in; }  [SIZE=2]Named.conf[/SIZE]
 [SIZE=2]// This is the primary configuration file for the BIND DNS server named.[/SIZE]
 [SIZE=2]//[/SIZE]
 [SIZE=2]// Please read /usr/share/doc/bind9/README.Debian.gz for information on the [/SIZE] 
 [SIZE=2]// structure of BIND configuration files in Debian, *BEFORE* you customize [/SIZE] 
 [SIZE=2]// this configuration file.[/SIZE]
 [SIZE=2]//[/SIZE]
 [SIZE=2]// If you are just adding zones, please do that in /etc/bind/named.conf.local[/SIZE]
 

 [SIZE=2]controls {[/SIZE]
 [SIZE=2]inet 127.0.0.1 port 953[/SIZE]
 [SIZE=2]allow { 127.0.0.1; } keys { "rndc-key"; };[/SIZE]
 [SIZE=2]};[/SIZE]
 

 [SIZE=2]include "/etc/bind/named.conf.options";[/SIZE]
 [SIZE=2]include "/etc/bind/named.conf.local";[/SIZE]
  [SIZE=2]include "/etc/bind/named.conf.default-zones";[/SIZE]

> My named.conf.options
                     p { margin-bottom: 0.08in; }  [SIZE=2]named.conf.options[/SIZE]
 [SIZE=2]//----------------------[/SIZE]
 [SIZE=2]options {[/SIZE]
 [SIZE=2]    directory "/var/cache/bind";[/SIZE]
 

 [SIZE=2]    // If there is a firewall between you and nameservers you want[/SIZE]
 [SIZE=2]    // to talk to, you may need to fix the firewall to allow multiple[/SIZE]
 [SIZE=2]    // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)[/SIZE]
 

 [SIZE=2]    // If your ISP provided one or more IP addresses for stable [/SIZE] 
 [SIZE=2]    // nameservers, you probably want to use them as forwarders.  [/SIZE] 
 [SIZE=2]    // Uncomment the following block, and insert the addresses replacing [/SIZE] 
 [SIZE=2]    // the all-0's placeholder.[/SIZE]
 

 [SIZE=2]    // forwarders {[/SIZE]
 [SIZE=2]    //     0.0.0.0;[/SIZE]
 [SIZE=2]    // };[/SIZE]
 

 [SIZE=2]    auth-nxdomain no;    # conform to RFC1035[/SIZE]
 [SIZE=2]    listen-on-v6 { any; };[/SIZE]
 [SIZE=2]};[/SIZE]
 

 [SIZE=2]forwarders {[/SIZE]
 [SIZE=2]# Replace the address below with the address of your provider’s DNS server[/SIZE]
 [SIZE=2]8.8.8.8;[/SIZE]
 [SIZE=2]};[/SIZE]
 > My example.com.db
                     p { margin-bottom: 0.08in; }  [SIZE=2]
[/SIZE]
 [SIZE=2]//------------------[/SIZE]
 [SIZE=2]// replace example.com with your domain name. 
[/SIZE]

[SIZE=2]example.com. IN SOA ns1.example.com. admin.example.com.[/SIZE]
 [SIZE=2]([/SIZE]
 [SIZE=2]// Do not modify the following lines![/SIZE]
 [SIZE=2]2007031001[/SIZE]
 [SIZE=2]28800[/SIZE]
 [SIZE=2]3600[/SIZE]
 [SIZE=2]604800[/SIZE]
 [SIZE=2]38400[/SIZE]
 [SIZE=2])[/SIZE]
 

 [SIZE=2]// Replace the following line as necessary:[/SIZE]
 [SIZE=2]// ns1 = DNS Server name[/SIZE]
 [SIZE=2]// mail = mail server name[/SIZE]
 [SIZE=2]// example.com = domain name[/SIZE]
 [SIZE=2]example.com. IN NS ns1.example.com.[/SIZE]
 [SIZE=2]example.com. IN MX 10 mail.example.com.[/SIZE]
 

 [SIZE=2]// Replace the IP address with the right IP addresses.[/SIZE]
 [SIZE=2]www IN A 192.168.1.120[/SIZE]
 [SIZE=2]mta IN A 192.168.1.121[/SIZE]
 [SIZE=2]ns1 IN A 192.168.1.122[/SIZE]
 What is wrong with my configuration ?

---

