---
title: "dhclient.conf manpage example contains error"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by tburt11 on 2011-05-11
There is an example in the manpage for dhclient.conf file that looks something like this:
 
interface "ep0" {
send host-name "andare.fugue.com";
send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
send dhcp-lease-time 3600;
supersede domain-name "fugue.com rc.vix.com home.vix.com";
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, host-name;
require subnet-mask, domain-name-servers;
script "/sbin/dhclient-script";
media "media 10baseT/UTP", "media 10base2/BNC";
}
 
The line:
 
supersede domain-name "fugue.com rc.vix.com home.vix.com";
 
is incorrect in two ways:
1) only one domain name should be specified for the option domain-name.
2) A multiple parameter option such as domain-search specified in this manner is also not correct syntax.
 
supersede domain-search "fugue.com rc.vix.com home.vix.com";
 
Will result in the following line in the resolv.conf file:
 
search fugue.com\032rc.vix.com\032home.vix.com
 
The correct syntax for the options should be:
 
supersede domain-name "fugue.com"; 
supersede domain-search "fugue.com" , "rc.vix.com" , "home.vix.com";

---

### Post by ningji on 2012-01-13
i got this
search home.vix.com. [www.com](www.com).

there's an extra dot for each domain.


> **tburt11 said:**
> There is an example in the manpage for dhclient.conf file that looks something like this:
 
interface "ep0" {
send host-name "andare.fugue.com";
send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
send dhcp-lease-time 3600;
supersede domain-name "fugue.com rc.vix.com home.vix.com";
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, domain-name-servers, host-name;
require subnet-mask, domain-name-servers;
script "/sbin/dhclient-script";
media "media 10baseT/UTP", "media 10base2/BNC";
}
 
The line:
 
supersede domain-name "fugue.com rc.vix.com home.vix.com";
 
is incorrect in two ways:
1) only one domain name should be specified for the option domain-name.
2) A multiple parameter option such as domain-search specified in this manner is also not correct syntax.
 
supersede domain-search "fugue.com rc.vix.com home.vix.com";
 
Will result in the following line in the resolv.conf file:
 
search fugue.com\032rc.vix.com\032home.vix.com
 
The correct syntax for the options should be:
 
supersede domain-name "fugue.com"; 
supersede domain-search "fugue.com" , "rc.vix.com" , "home.vix.com";

---

### Post by DennisDamenace on 2012-02-17
I'm seeing this same issue. Our DHCP server is giving domain-search list in DHCP option 119 and my /etc/resolv.conf ends up listing those additional domains with a tailing dot and it breaks things up. If I remove the dots manually, I can surf with the hostnames only, but every time I connect to the network here I need to do this or it doesn't work.
I'm not sure what causes the tailing dots to appear in there, because they're not on the DHCP server and other users (with MAC or Windows workstations) won't get them. I couldn't find any tips where to change this behaviour. Is it a bug?

---

