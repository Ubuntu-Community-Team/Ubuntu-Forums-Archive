---
title: "DNS servers"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by nidelius on 2009-03-05
Hi!

I'm using ubuntu 8.10 with wireless connection.
I have problems with the DNS servers
The actual problem is based on that my home router have problem forwarding linux DNS requests (meaning Internet feels like 56K modem until the DNS is resolved. I have tested a lot and it seems to be the only way it can be true. Because it works in windows.
So my router gives me it's ip as DNS and second and thrid option is the DNS servers from my ISP so here is what the file lookes like when I recieve the settings from the router. 

```
example of /etc/resolv.conf

192.168.1.1
ISP-DNS1
ISP-DNS2
```

I then change this in
```
/etc/dhcp3/dhclient.conf

prepend domain-name-servers ISP-DNS1,ISP-DNS2;
```

```
My /etc/resolv.conf Then lookes like this which is good.
ISP-DNS1
ISP-DNS2
```

OK, I want to bring my laptop to school. So I manually set up the school DNS also in the dhclient.conf

```
prepend domain-name-servers SCHOOLDNS(194.47.161.8),ISPDNS1,ISPDNS2;

My /etc/resolv.conf 
SCHOOLDNS
ISP-DNS1
ISP-DNS2
```

OK everything works fine in school. Anywhere else? no.. So I have to manually switch back and forth all the time. Is the operating system not supposed to try the second dns of the resolv.conf if it doesn't get a response from the first one? It seems like thats what it's not doing. Since it's not working when I have the local address as DNS and also not when I am outside school and the schoolDNS (that's probably blocking ips out of school to use it) set, it doesn't seem to connect to my ISPs DNS servers even though they are in resolv.conf. For better user experience I think that the DNS servers should be pinged or tested and the fastest one should be prefered by the operatingsystem.

---

