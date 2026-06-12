---
title: "DNS/BIND appears to work properly but..."
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Icky_Ev on 2009-06-24
Thank you in advance. :KS

I am still working to set up my server as a local DNS, so the Windows boxes on the LAN can access it via a FQDN instead of its IP. The LAN has no internet connection. 

I went through the excellent BIND/DNS tutorial and can dig/ping the server, but the other computers still cannot access it. I have set up pretzel as a DNS server, and included its IP address in their network settings. 

I'll post the results of dig, but will hold off posting tons of other code snippets as I'm not sure what you'd want to see considering dig returns "NOERROR"

Just glancing at it I notice there is no "AUTHORITY" response. Is that a potential red flag?

```

; <<>> DiG 9.5.1-P2 <<>> pretzel.lan
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 8486
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;pretzel.lan.            IN    A

;; ANSWER SECTION:
pretzel.lan.        10    IN    A    24.28.193.9

;; Query time: 60 msec
;; SERVER: 24.93.41.127#53(24.93.41.127)
;; WHEN: Tue Jun 23 23:28:12 2009
;; MSG SIZE  rcvd: 62

```

---

### Post by jhannah on 2009-06-24
It sounds like your are just missing a SOA record and or NS records for that zone. What does the zone file look like?

The status of NOERROR is perfectly normal and means simply that. :)

To give you an example, your zone should look something like this:

```

$ORIGIN pretzel.lan
$TTL 86400

@    IN    SOA    server.pretzel.lan. hostmaster.pretzel.lan. (
                        2009062499 ; serial
                        21600          ; refresh after 6 hours
                        3600            ; retry after 1 hour
                        604800         ; expire after 1 week
                        86400 )         ; TTL of 1 day

             IN    NS server.pretzel.lan.

             IN    A   24.28.193.9
server    IN    A   24.28.193.9
box1      IN    A   1.2.3.4

```That should do the trick, just keep in mind whenever your modify the zone, you need to update the serial (just add 1 to it) and reload bind or use 'rndc reload' or 'rndc reload [zone]'.

Let me know if that helps.

---

### Post by Icky_Ev on 2009-06-24
Thanks for the feedback! I'll post back- not sitting at the server right now to supply snippets. :)

---

