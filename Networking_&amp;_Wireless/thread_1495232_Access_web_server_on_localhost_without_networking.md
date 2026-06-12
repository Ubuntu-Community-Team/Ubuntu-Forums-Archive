---
title: "Access web server on localhost without networking?"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by linfidel on 2010-05-27
I have a laptop with Apache, MySQL, PHP, etc, and I'm able to work on web programming on my local server while at home, connected to my network.  But I would like to be able to work on the local websites when I'm not connected to any networks, both for demonstrating a site, or simply working on it.

I was surprised to find that I could not connect to localhost at all without a network connection.  I tried my normal Google for a solution, but, of course, that was futile without a network. :-)

Now, I'm at home, and of course, it works because I have wireless.  I don't really want to disconnect that to figure it out, so I thought maybe some nice soul here might know how to do this.  Surely it can't be hard, can it?  But, it's certainly not obvious.  Anyone know how to do this?

---

### Post by diesch on 2010-05-27
What do you mean by "ould not connect to localhost"? What does
```
 dig localhost
``` on the command line print?

By default you can connect to localhost without any external network, and apache is listening on localhost.

---

### Post by linfidel on 2010-05-28
> **diesch said:**
> What do you mean by "could not connect to localhost"? What does
```
 dig localhost
``` on the command line print?
Sorry for my vagueness there - I feel like such a newbie.  Normally, I'm pretty good at troubleshooting, but I'm really not up to speed with Linux networking.  I've been unfortunate in that I haven't had any hard problems, so I've never been forced to learn more.

In answer to the 1st question, I meant that using a browser, when I entered "http://localhost" (or any of my usual local URLs), I got an error from the browser - not from Apache.  After getting connected to the wireless network that was available, I was then able to connect to the web server.

Trying "http://127.0.0.1/" also gave the same results.  Error was 105, "ERR_NAME_NOT_RESOLVED, The server could not be found." But I was able to ping localhost successfully.

In answer to your 2nd question... I'll post a 2nd response from the laptop - right now I'm on my desktop, as usual. 

Here is what I get while connected to the home wireless and wired (via a 2wire gateway):
```
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 5539
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;localhost.			IN	A

;; ANSWER SECTION:
localhost.		0	IN	A	127.0.0.1

;; AUTHORITY SECTION:
localhost.		41728	IN	NS	homeportal.gateway.2wire.net.

;; ADDITIONAL SECTION:
homeportal.gateway.2wire.net. 41728 IN	A	192.168.1.254

;; Query time: 14 msec
;; SERVER: 192.168.1.254#53(192.168.1.254)
;; WHEN: Fri May 28 09:16:22 2010
;; MSG SIZE  rcvd: 119
```

With wireless disabled on the gateway, I get a delay, then
```
;<<>> DiG 9.6.1-P2 <<>> localhost
;; global options: +cmd
;; connection timed out; no servers could be reached
```


Thanks for your help so far.

> **diesch said:**
> By default you can connect to localhost without any external network, and apache is listening on localhost.
That's what I was assuming.  I was surprised when it didn't work.  Maybe I should check my hosts file, since I've messed with it a bit to add local development domains for sites I'm working on.

---

### Post by linfidel on 2010-05-28
I found the problem. 

It turns out to be an issue with Google Chrome, which I use on the laptop because it's faster.  I found that it works with Firefox.  Then I learned there is a known bug/issue that recently came up with Chrome.  It has to do with disabling IPV6, and the workaround is to run chrome with a command line ending in "--enable-ipv6", which I confirmed did work.

Sorry for any confusion or wasted effort on anyone's part.

---

