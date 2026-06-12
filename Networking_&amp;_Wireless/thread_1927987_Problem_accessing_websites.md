---
title: "Problem accessing websites"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by stavih on 2012-02-19
Ubuntu 10.4 lts 64bit desktop.  As time goes by, I'm finding I am able to access fewer and fewer websites that I normally visit.  First I was unable to access sites like tigerdirect; then amazon stopped working.  Now I cant even access Engadget and Dailymail.co.uk.  I have TimeWarner broadband.  I have tried multiple browsers (Firefox. Chromium, Seamonkey, Epiphany) all with the same result.  Anybody experiencing this?  Got any clues?  Any intelligent questions for more info?

---

### Post by roelforg on 2012-02-20
I was gonna quote my guide for issues, but this one is special.
Try flushing your routers DNS cache, if it doesn't work, ask your ISP.

Also try the following:
Run "dig amazon.com" (no quotes) in your terminal;
Mine can access amazon.com and gives this output (compare IP addresses, if they're different there are some serious dns issues at your place)
```

; <<>> DiG 9.7.3 <<>> amazon.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 34771
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 10, ADDITIONAL: 10

;; QUESTION SECTION:
;amazon.com.            IN    A

;; ANSWER SECTION:
amazon.com.        60    IN    A    72.21.214.128
amazon.com.        60    IN    A    72.21.194.1
amazon.com.        60    IN    A    72.21.211.176

;; AUTHORITY SECTION:
amazon.com.        3600    IN    NS    pdns2.ultradns.net.
amazon.com.        3600    IN    NS    ns2.p31.dynect.net.
amazon.com.        3600    IN    NS    ns4.p31.dynect.net.
amazon.com.        3600    IN    NS    pdns6.ultradns.co.uk.
amazon.com.        3600    IN    NS    ns3.p31.dynect.net.
amazon.com.        3600    IN    NS    ns1.p31.dynect.net.
amazon.com.        3600    IN    NS    pdns1.ultradns.net.
amazon.com.        3600    IN    NS    pdns4.ultradns.org.
amazon.com.        3600    IN    NS    pdns3.ultradns.org.
amazon.com.        3600    IN    NS    pdns5.ultradns.info.

;; ADDITIONAL SECTION:
ns1.p31.dynect.net.    64619    IN    A    208.78.70.31
ns2.p31.dynect.net.    64619    IN    A    204.13.250.31
ns3.p31.dynect.net.    64619    IN    A    208.78.71.31
ns4.p31.dynect.net.    64619    IN    A    204.13.251.31
pdns1.ultradns.net.    3537    IN    A    204.74.108.1
pdns1.ultradns.net.    3537    IN    AAAA    2001:502:f3ff::1
pdns2.ultradns.net.    3537    IN    A    204.74.109.1
pdns3.ultradns.org.    3537    IN    A    199.7.68.1
pdns5.ultradns.info.    3537    IN    A    204.74.114.1
pdns6.ultradns.co.uk.    3537    IN    A    204.74.115.1

;; Query time: 67 msec
;; SERVER: 192.168.0.104#53(192.168.0.104)
;; WHEN: Mon Feb 20 21:06:19 2012
;; MSG SIZE  rcvd: 502


```

Good luck

---

### Post by stavih on 2012-02-21
> **stavih said:**
> Problem accessing websites

  Solved: Found instructions for changing DNS servers to open source.  This solved my access problems. Here: [https://store.opendns.com/setup/device/ubuntu](https://store.opendns.com/setup/device/ubuntu)

---

### Post by roelforg on 2012-02-21
Glad to hear that!

If you find any issues,
try these dns servers:
8.8.8.8
8.8.4.4
Those are google's.

Your problem might have been this:
Amazon changes their IP's all the time,
that's why they've set their DNS TTL (the time any dns-server is allowed to cache the ip's) really low.
However the servers from some ISP's ignore that, causing DNS entry's (like amazon.com) to point to empty ip's.

---

