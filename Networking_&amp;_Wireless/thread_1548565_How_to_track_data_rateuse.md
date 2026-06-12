---
title: "How to track data rate/use?"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by radtek on 2010-08-08
I'm sure this is simple but I haven't a clue how to do it other than System Monitor, which only displays for the total uptime.:(

I want to see what my total network data use is in Bytes (GB, MB, or KB) downloaded/uploaded **for the month or any given date range.**

Rationale is I want to use wireless tethering from my phone to replace my broadband connection at home. At the moment my phone contract gives me unlimited data access, however if I were to sign a new contract today this would drop to 2 GB a month with hefty overage charges. 

I need to get a realistic idea of what my actual home usage is before committing to anything.
 
TIA 

Rad

---

### Post by radtek on 2010-08-11
[bump]

Hey I found a simple program called vnstat. Sort-of works. Can get averages etc. I'm having a problem:

```
radtek@tosh:~$ vnstat 
 eth0: Not enough data available yet.
or
radtek@tosh:~$ vnstat -h
 eth0: Not enough data available yet.

```

It's supposed to write to a log "eth0" in /var/lib/vnstat? Can't read this one.

Is there any other similar programs out there that work well?

---

