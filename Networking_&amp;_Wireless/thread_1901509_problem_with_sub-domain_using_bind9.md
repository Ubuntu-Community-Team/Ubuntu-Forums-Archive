---
title: "problem with sub-domain using bind9"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by weloki on 2011-12-28
I'm trying to set up a sub-domain within a private network and I'm using bind9 on the authoritative DNS server for the zone. I believe everything is mostly working but I think there's an issue uncovered in preliminary testing... the sub-domain I'm trying to get control of still can't be found.

The output for dig -x 127.0.0.1 on the name server itself looks OK:[FONT=Courier New][SIZE=1]
[/SIZE][/FONT]
[FONT=Courier New][SIZE=1][FONT=Courier New][SIZE=1]; <<>> DiG 9.7.0-P1 <<>> -x 127.0.0.1
 ;; global options: +cmd
 ;; Got answer:
 ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 18185
 ;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 2
  
 ;; QUESTION SECTION:
 ;1.0.0.127.in-addr.arpa.        IN    PTR
  
 ;; ANSWER SECTION:
 1.0.0.127.in-addr.arpa.    604800    IN    PTR    localhost.
  
 ;; AUTHORITY SECTION:
 127.in-addr.arpa.    604800    IN    NS    localhost.
  
 ;; ADDITIONAL SECTION:
 localhost.        604800    IN    A    127.0.0.1
 localhost.        604800    IN    AAAA    ::1
  
 ;; Query time: 0 msec
 ;; SERVER: 192.168.2.99#53(192.168.2.99)
 ;; MSG SIZE  rcvd: 121

[/SIZE][/FONT][/SIZE][/FONT] When I use dig to query the DNS name server about itself it seems right to me:

[FONT=Courier New]; <<>> DiG 9.7.0-P1 <<>> ns.dev.example.org
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 45149
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;ns.dev.example.org.    IN    A

;; ANSWER SECTION:
ns.dev.example.org. 604800 IN    A    192.168.2.99

;; AUTHORITY SECTION:
dev.example.org.    604800    IN    NS    ns.dev.example.org.

;; Query time: 0 msec
;; SERVER: 192.168.2.99#53(192.168.2.99)
;; MSG SIZE  rcvd: 73
[/FONT]
However, when I use dig to query the actual sub-domain there is no answer section and I see the line:
[FONT=Courier New];; flags: qr aa rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0
[/FONT]
Using dig to query a different name server about the host ns.dev.example.org turns up the same thing.

Also, if I use nslookup for the sub-domain it returns:
[FONT=Courier New]** server can't find dev.example.org: NXDOMAIN[/FONT]

This is the zone file:

[FONT=Courier New]$TTL    604800 
dev.example.org.    IN    SOA    ns.dev.example.org. admin.dev.example.org. (
                 16        ; Serial
             604800        ; Refresh - 7 days
              86400        ; Retry - 24 hours
            2419200        ; Expire - 28 days
             604800 )    ; Negative Cache TTL
;
    IN    NS    ns.dev.example.org.
dev.example.org    IN A    192.168.2.99
ns    IN    A    192.168.2.99
desktop    IN    A    192.168.2.74[/FONT]

---

### Post by Doug S on 2011-12-28
I'm not an expert on bind9, but your zone file doesn't look right to me. Try this:
 
```
 
$TTL 604800
@ IN SOA dev.example.org. admin.dev.example.org. (
17 ; Serial
604800 ; Refresh - 7 days
86400 ; Retry - 24 hours
2419200 ; Expire - 28 days
604800 ) ; Negative Cache TTL
   IN  A 192.168.2.99
;
@  IN NS ns.dev.example.org.
ns IN A 192.168.2.99
desktop IN A 192.168.2.74

```

---

### Post by weloki on 2011-12-29
Thanks for the response Doug. I tried making the changes in the zone file, checked the syntax, restarted the bind service and the same issue is still there. I had tried different configurations myself, but of course to no avail. 
To describe the issue again, this time using ping... I can ping the host itself with it's FQDN, ns.dev.example.org, and I get an expected response with its IP properly resolved. However if I try to ping the sub-domain, dev.example.org, it returns 
"ping: unknown host dev.example.org".[FONT=Courier New][/FONT]

---

### Post by d3v1150m471c on 2011-12-29
[http://cr.yp.to/djbdns/blurb/unbind.html](http://cr.yp.to/djbdns/blurb/unbind.html) enjoy.

---

### Post by weloki on 2011-12-29
Another note: when I point my workstation to the name server in question, and only that server, (as in /etc/resolv.conf), it provides DNS services to the workstation just fine, so it's functioning on that level. 
Also it appears the DNS root servers do not have any of my name server's records, so I don't think my DNS information is being propagated/cached anywhere on the internet.

---

### Post by d3v1150m471c on 2011-12-29
Your last post is 43 minutes old. That's 43 minutes from when you should have switched to djbdns.

[http://cr.yp.to/djbdns/blurb/easeofuse.html](http://cr.yp.to/djbdns/blurb/easeofuse.html)

---

### Post by Doug S on 2011-12-29
> **weloki said:**
> Another note: when I point my workstation to the name server in question, and only that server, (as in /etc/resolv.conf), it provides DNS services to the workstation just fine, so it's functioning on that level. 
Also it appears the DNS root servers do not have any of my name server's records, so I don't think my DNS information is being propagated/cached anywhere on the internet.
Yes, thats right, your DNS wouldn't be propagated on the internet. I guess I misunderstood your requirements. Your original posting mentioned "a sub-domain within a private network", which I had interprated as your DNS was acting just locally. Your workstation should point to your local DNS, with others as backups. Your DNS server should also have forwarders, and it should handle all DNS requests for your LAN.
Now, if you want your DNS to be the authority for your public domain, then you will have to set the proper records at your Registrar to point to your DNS server. (in my case, my DNS server is not public facing, it only handles my LAN). There were some recent threads on this subject, one here: [http://ubuntuforums.org/showthread.php?t=1855739](http://ubuntuforums.org/showthread.php?t=1855739)
 
Hope this helps

---

### Post by weloki on 2011-12-29
Thanks again Doug for your response. Maybe I should attempt to clarify a bit... when I said we want to create a sub-domain within a private network I meant that our organization has websites both public-facing on the internet and private ones on our intranet. So the domain names of our public sites are like example.org and our private ones are like test.example.org. Now we just need another sub-domain like dev.example.org, but it's on a separate private network that we do not administer. 
I do want this DNS server to be authoritative for the new sub-domain. What I've recently done is sent a request to the admin that handles the DNS services for the example.org domain. As far as I understand that series of name servers they control should be updated to have records that point to our new DNS server since only those name servers (for example.org) would have any knowledge of the box that is authoritative for dev.example.org. That's why I think I've noticed that bind is working in every other regard except the server itself isn't recorded in DNS as a whole on the internet, so nobody would be able to reach the machine with just its name. Hopefully this is actually the case.

---

### Post by SeijiSensei on 2011-12-31
> **weloki said:**
> As far as I understand that series of name servers they control should be updated to have records that point to our new DNS server since only those name servers (for example.org) would have any knowledge of the box that is authoritative for dev.example.org. That's why I think I've noticed that bind is working in every other regard except the server itself isn't recorded in DNS as a whole on the internet, so nobody would be able to reach the machine with just its name. Hopefully this is actually the case.

Sounds right to me.  The server for example.org needs to have an NS record for dev.example.org that points to the nameserver authoritative for the subdomain.  Until the admin for example.org fixes that, requests for hosts in dev.example.org won't be directed to your server for resolution.

---

