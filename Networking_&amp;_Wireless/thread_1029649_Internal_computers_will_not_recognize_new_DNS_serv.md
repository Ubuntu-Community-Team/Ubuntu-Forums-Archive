---
title: "Internal computers will not recognize new DNS server"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by borramakot on 2009-01-03
I just set up an Ubuntu workstation with a DNS server, in this case MaraDNS
(though BIND also did this). I want the DNS to resolve the names of ~10 workstations in a private office, with the .office extension. Right now, if I ping those computers with the workstation which hosts the DNS, the IP address resolves fine. 

But, if I edit the resolv.conf files of the other computers to get their DNS from my server, it doesn't work.

Any ideas?

---

### Post by wmdiem on 2009-01-03
try to do a dns lookup from a client
dig hostnametolookup

you can also try netcat to see whether the server is even listening
nc serverip 53
if it just sits there your good. otherwise you will get an error.

---

### Post by borramakot on 2009-01-04
When I run 
     dig neptune.office
it tells me
     ; <<>> DiG 9.5.0-P2 <<>> neptune.office
     ;; global options:  printcmd
     ;; connection timed out; no servers could be reached

Neptune is my name server.
When I run 
     dig venus.office
it tells me
     ; <<>> DiG 9.5.0-P2 <<>> venus.office
     ;; global options:  printcmd
     ;; Got answer:
     ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 29883
     ;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

     ;; QUESTION SECTION:
     ;venus.office.			IN	A

     ;; ANSWER SECTION:
     venus.office.		0	IN	A	208.69.36.132

     ;; Query time: 102 msec
     ;; SERVER: 192.168.0.1#53(192.168.0.1)
     ;; WHEN: Sun Jan  4 11:07:46 2009
     ;; MSG SIZE  rcvd: 46

None of those numbers are Venus's IP address.

When I run
     nc serverip 53
it tells me
     serverip: forward host lookup failed: Unknown host : Connection timed out
     

I can ping any of these servers fine by their IP address or hosts file.

What am I doing wrong?

---

### Post by wmdiem on 2009-01-04
sorry, for the netcat command, serverip is meant to be replaced with the ip address of your dns server. but i don't think you need to run it since, from the other results, it seems to be listening.

---

### Post by borramakot on 2009-01-06
When I run 

nc 192.168.0.2 53

(192.168.0.2 being neptune, the nameserver)

from neptune, it tells me

(UNKNOWN) [192.168.0.2] 53 (domain) : Connection refused

The same thing happens if I do 127.0.0.1 instead of 192.168.0.2

But, I can still ping computers in my db.office file that are not in my hosts file.

I dont know of any firewall. How would I check for one?

---

### Post by wmdiem on 2009-01-14
The name server you are getting is 192.168.0.1

```
;; Query time: 102 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Sun Jan 4 11:07:46 2009
;; MSG SIZE rcvd: 46
```

This suggests that your computers are satisfying their DNS needs from some other source (192.168.0.1, a local router?) not from 192.168.0.2.
I have never configured a local DNS server or worked with linux firewalls, so I don't know what to tell you, but whatever it is your DNS server isn't listening for and getting incoming requests. 
I assume it is properly bound (to the internal IP) and all that. Other than than I can just guess that there is a firewall.

EDIT: Also, if you are manually editing the host file, I am confused where the 192.168.0.1 is coming from, unless you are leaving it as a second DNS server. Maybe you have DHCP and it is overwriting your host file occasionally?

---

