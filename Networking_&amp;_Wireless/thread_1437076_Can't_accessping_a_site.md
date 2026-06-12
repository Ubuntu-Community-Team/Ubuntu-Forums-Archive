---
title: "Can't access/ping a site"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by Cyked on 2010-03-23
Trying to access 67.15.245.6 (its a forum site).  I can't get to it from home for over a month now.  I can't ping it, but I can ping obvious things like google.  Tracert isn't working at all.  Once it hits the lightspeed.frokca.sbcglobal.net hop it just dies like ATT isn't allowing traceroutes.  I've been using Tor as a work around.  About 3 months ago I basically had the same issue with openbittorrent.com's site.

I have a linux server and windows XP box.  I can't ping the above IP nor tracepath/traceroute to the IP from my linux box.

I have ATT uverse. Any thoughts?

EDIT:  The site is hometheaterlounge.com (The IP won't do you much and its just the IP of the site host).  Just a shot in the dark posting here for ideas one what else to try to figure out what is going on.

---

### Post by pricetech on 2010-03-23
Nothing other than the obvious, that you or your network are being blocked for some reason.  What's your IP ??

---

### Post by Cyked on 2010-03-24
Out of curiosity, why would you need my IP?

---

### Post by pricetech on 2010-03-25
I forget.  I had something in mind, but I've slept since then.

---

### Post by Cyked on 2010-08-19
I hate resurrecting old threads, but I've noticed for one reason or another I can't traceroute to ANYTHING from my linux box.  I still can't access the site referenced now and in the original post.

So I have a few issues and just now getting around to looking into it.

My setup:

running 2 linksys routers with tomato
Router 1 (WRT54G): connected to att uverse gateway. The gateway passes my external IP address to this router. IP is .2.1

Router 2 (WRT54GL): connected to Router 1 as a wireless client with 2 machines wired to it (windows XP and Ubuntu). IP is .2.2 with gateway set as .2.1.

Computers: both machines are static IP as .2.101 and .2.102.

Issue 1: For the longest time I can not access hometheaterlounge.com. It just times out and have not been able to figure out why.
I can ping and tracert the site from windows and I can resolve the the IP in linux, but that's ALL I can do from either machine. Here is what happens though from the Windows tracert


```
Tracing route to hometheaterlounge.com [67.15.245.6]
over a maximum of 30 hops:

  1     1 ms     1 ms     1 ms  [192.168.2.1]
  2     *        *        *     Request timed out.
  3    23 ms    22 ms    25 ms  99-185-0-2.lightspeed.frokca.sbcglobal.net [99.1
85.0.2]
  4    24 ms    22 ms    22 ms  75.29.76.196
  5     *        *        *     Request timed out.
  6     *       23 ms    22 ms  75.29.64.76
  7    27 ms     *        *     75.29.64.14
  8    23 ms    22 ms    22 ms  151.164.38.36
  9    27 ms    26 ms    25 ms  ppp-151-164-52-207.rcsntx.swbell.net [151.164.52
.207]
 10    27 ms    26 ms    26 ms  xe-0-2-0-5.r07.snjsca04.us.bb.gin.ntt.net [129.2
50.9.121]
 11    26 ms    26 ms    26 ms  ae-8.r21.snjsca04.us.bb.gin.ntt.net [129.250.5.5
6]
 12    83 ms    68 ms    69 ms  ae-5.r21.dllstx09.us.bb.gin.ntt.net [129.250.4.2
4]
 13     *        *        *     Request timed out.
 14    68 ms    68 ms    68 ms  xe-7-3.r01.dllstx09.us.ce.gin.ntt.net [157.238.2
24.182]
 15    72 ms    72 ms    72 ms  et1-1.ibr01.hstntx2.theplanet.com [70.87.253.50]

 16    72 ms    72 ms    72 ms  2-2.dsr02.hstntx2.theplanet.com [74.55.252.38]
 17    74 ms    73 ms    72 ms  po2.car12.hstntx2.theplanet.com [74.55.252.210]

 18     *        *        *     Request timed out.
 19     *        *        *     Request timed out.
 20     *        *        *     Request timed out.

```


Issue 2: No idea how long this has really been going on. When I tracert/traceroute from the machines I get different things.

Here is what I get from computer 1 (windows xp):


```
Tracing route to google.com [74.125.19.104]
over a maximum of 30 hops:

  1     1 ms     1 ms     1 ms      [192.168.2.1]
  2     *        *        *     Request timed out.
  3   814 ms   597 ms   502 ms  99-185-0-2.lightspeed.frokca.sbcglobal.net [99.1
85.0.2]
  4    24 ms    22 ms    24 ms  75.29.76.196
  5    27 ms    37 ms    23 ms  75.29.64.81
  6     *        *        *     Request timed out.
  7     *        *        *     Request timed out.
  8    23 ms    22 ms    22 ms  151.164.38.36
  9    26 ms    33 ms    27 ms  151.164.38.18
 10    81 ms    26 ms    29 ms  151.164.251.222
 11    71 ms    42 ms    28 ms  216.239.49.250
 12    28 ms    31 ms    39 ms  209.85.249.30
 13    34 ms    28 ms    27 ms  nuq04s01-in-f104.1e100.net [74.125.19.104]

Trace complete.

When I trace from computer 2 (ubuntu)... this happens for every site:
Code:

 traceroute google.com
traceroute to google.com (74.125.19.104), 30 hops max, 40 byte packets
 1  (192.168.2.1)  2.065 ms  2.968 ms  3.090 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
30 * * *
```

nslookup from computer 2 ubuntu:


```
nslookup google.com
Server:         192.168.2.1
Address:        192.168.2.1#53

Non-authoritative answer:
Name:   google.com
Address: 74.125.19.99
Name:   google.com
Address: 74.125.19.103
Name:   google.com
Address: 74.125.19.104
Name:   google.com
Address: 74.125.19.147
```



I'm sure more details are needed, but will start with this. My networking knowledge is laughable, I'm sure, so any help is greatly appreciated.

---

### Post by Cyked on 2010-08-31
For anyone that cares.....  It works now.  I finally got around to sending emails to the hosting companies.  My brother who runs the forum ended up having to email them to check my IP since is the site owner and has an admin account.  Sure enough my IP was blocked, for DOS apparently.  No idea where that came from, but I guess my machine could have been infected and was causing screwy things (my windows box I mean).

At any rate, that works, BUT I still can't trace anything from linux.

---

