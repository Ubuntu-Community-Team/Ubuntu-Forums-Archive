---
title: "DNS resolution on a home network"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by vas12 on 2008-12-13
Hi,

This might not fit the regular linux problems posted on this group. But it still fits. If not direct me to the correct group. Any help is appreciated. I run my web server on ubuntu.

I have a hostname (url) I bought and have a dynamic dns service that does the dns resolution for me. Lets say my hostname is A.com, it resolves from the outside to my home router. Any request from the outside comes to my router on which I forward the port to the machine with the web server. The router also is the DNS server for the entire home network.
But from inside the network, A.com goes to my wireless router which resolves it to itself but never gets forwarded properly to the machine. That is because the port forwarding rules only apply to incoming requests from outside.
How do you resolve this? Do I have to set up a DNS server somewhere on my network? Is there another solution?

Thanks,
Vas

---

### Post by generic_idea_machine on 2008-12-24
I am running into the exact same problem. 

Couple of things I've tried:

_What works:_
[LIST]
[*]Accessing the host/webserver externally
[/LIST] :(


_What doesnt work:_
[LIST]
[*]Accessing the host/webserver by the local i.p address (10.1.x.x or 192.1.x.x) or hostname when the "**use=web**" feature is enabled in the ddclient.conf file. 
[/LIST]

I decided to read up a bit more on the ddlcient.conf file and came across the following page on the dyndns website [ [link]("http://www.dyndns.com/support/kb/using_ddclient_with_dyndns_services.html") ]

I believe if we use one of the following options below, then we should be able to access the url on the internal network:
[LIST]
[*]bind dyndns to a local interface (dsl/cable hooked up to the machine directly)
[*]using a linksys router (apparently it has a status page that dyndns can query for the external i.p)
[*]using a fw mechanism of some sort
[/LIST]
  You'd still have to edit the ddclient.conf file to specify the method you are using. 

 If you are using the web option ddclient.conf file and would like to access the host/url to make some changes on the internal network. Well one way I can think of doing this is to actually use the "bind to interface options" in the ddclient.conf file:
 ```
## via hardware interface (if you don't have a router/firewall)
#use=if, if=eth0

```
 However this will most certainly result into downtime for the website, besides it takes some time for dns to propagate when you switch it back to the "use=web" option

Please let me know if you or someone else has found a working solution

---

### Post by dmizer on 2008-12-24
> **vas12 said:**
> Hi,

This might not fit the regular linux problems posted on this group. But it still fits. If not direct me to the correct group. Any help is appreciated. I run my web server on ubuntu.

I have a hostname (url) I bought and have a dynamic dns service that does the dns resolution for me. Lets say my hostname is A.com, it resolves from the outside to my home router. Any request from the outside comes to my router on which I forward the port to the machine with the web server. The router also is the DNS server for the entire home network.
But from inside the network, A.com goes to my wireless router which resolves it to itself but never gets forwarded properly to the machine. That is because the port forwarding rules only apply to incoming requests from outside.
How do you resolve this? Do I have to set up a DNS server somewhere on my network? Is there another solution?

Thanks,
Vas

I just change the hosts file on the client. So, if I wanted to access my server from my laptop while I was connected to my internal network, my laptop's /etc/hosts file would look like this:
```
192.168.0.13    A.com B.com C.net

127.0.0.1       localhost
127.0.1.1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

When I take my laptop to the coffee shop, I just comment out the server line, so the /etc/hosts file looks like this:
```
#192.168.0.13    A.com B.com C.net

127.0.0.1       localhost
127.0.1.1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by generic_idea_machine on 2008-12-24
> **dmizer said:**
> I just change the hosts file on the client. So, if I wanted to access my server from my laptop while I was connected to my internal network, my laptop's /etc/hosts file would look like this:
```
192.168.0.13    A.com B.com C.net

127.0.0.1       localhost
127.0.1.1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

When I take my laptop to the coffee shop, I just comment out the server line, so the /etc/hosts file looks like this:
```
#192.168.0.13    A.com B.com C.net

127.0.0.1       localhost
127.0.1.1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Thanks! 

It works and works well :guitar:

---

### Post by dmizer on 2008-12-24
Yup, and it works the same way with Windows or Mac as well. The Windows hosts file located here: %SystemRoot%\system32\drivers\etc\hosts

---

### Post by ziesemer on 2008-12-24
The best way is to make the process transparent, without needing to edit the client's configuration.

As was already mentioned, the main issue is currently that "the port forwarding rules only apply to incoming requests from outside".  This can be fixed, at least with any quality firewall and/or any one based on iptables.

In this case, the iptables rule responsible for forwarding is probably keyed to the LAN interface using "-i $WAN_IF" or something similar.  Instead, it should be reset to match by the WAN's IP address, so it doesn't matter if the request is coming from the LAN or the WAN, as long as it's directed to the WAN's IP address and not the router's LAN IP.  This can be done using "-d $WAN_IP".  Here's one way of obtaining the WAN_IP in the same iptables script:

```
WAN_IP=$(ifconfig $WAN_IF | sed -n 's/ *inet addr:\([0-9.]*\).*/\1/p')
```

Just be aware that some of the filter chains that are pre-configured and suggested for use on some iptables-based firewalls are fed from a rule that already contains "-i $WAN_IF" or something similar, meaning that you might need to find and put these suggestions in a parent rule.

---

### Post by generic_idea_machine on 2008-12-24
Interesting

Thanks Ziesemer

Will try it out over the Holidays (When I get some time :) )

---

