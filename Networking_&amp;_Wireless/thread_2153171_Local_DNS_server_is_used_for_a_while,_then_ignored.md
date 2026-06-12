---
title: "Local DNS server is used for a while, then ignored - Why?"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by thehud on 2013-06-10
Hi Guys,

I've a strange problem that (I think) is DNS related. 

I use a DNS server in my office to provide host entries for various (web development) sandboxes on my machine (different hardware to dns server) to my colleagues. I also use this to resolve my boxes rather than continually editing my host file.

All works fine for a while, but then I'll refresh or navigate to a fresh page on a sandbox, and I'll get a "Oops! Google Chrome could not find a.cb.jh.local". If I dig the hostname, I see a response that looks like it didn't come from my server:

```

; <<>> DiG 9.8.1-P1 <<>> a.cb.jh.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NXDOMAIN, id: 7069
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0


;; QUESTION SECTION:
;a.cb.jh.local.            IN    A


;; AUTHORITY SECTION:
.            3445    IN    SOA    a.root-servers.net. nstld.verisign-grs.com. 2013061000 1800 900 604800 86400


;; Query time: 15 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Jun 10 13:42:35 2013
;; MSG SIZE  rcvd: 106

```

When the host does resolve, dig gives me:
```
; <<>> DiG 9.8.1-P1 <<>> a.cb.jh.local
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3728
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1


;; QUESTION SECTION:
;a.cb.jh.local.            IN    A


;; ANSWER SECTION:
a.cb.jh.local.        38400    IN    A    192.168.1.200


;; AUTHORITY SECTION:
local.            38400    IN    NS    local.


;; ADDITIONAL SECTION:
local.            38400    IN    A    192.168.1.200


;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Mon Jun 10 13:33:42 2013
;; MSG SIZE  rcvd: 77

```
Where can I look to find more information on this, or what flags could I pass to dig to further diagnose this? No one else has noticed this, but the problem seems sporadic and short lived, and is mostly really annoying to me. I'm mainly trying to work out if it's the DNS server's configuration, or my machine's resolver playing up.

Thanks to anyone who can help!

James.

---

### Post by SeijiSensei on 2013-06-10
It could be a resolver problem, or your DNS server could be intermittently unavailable over the network.  What version of Ubuntu is running on the client?  9.04 or something more recent?  What's the contents of /etc/resolv.conf?  Is there any reason to think that connectivity to the DNS server is dicey?

The difference in replies, in case it wasn't clear to you, is that your server did not respond to the query in the top example, and it was sent to a root nameserver for processing.  That would only happen if your local server is unavailable for some reason, and you have other public servers in the list in resolv.conf.

---

### Post by thehud on 2013-07-16
Sorry to be so late back - Thanks for the tips. 

The client is 12.04, And I believe the server is the same. Can't check right now, as I'm not in the office. 

What I did find out, however, is that I'd been using a static IP setup, and after a recent office move, the network guy changed IP assignments - giving away the ones I'd been using to be assigned to the boss' iPhone. (I'd been noticing other weird connectivity problems and finally asked him if he'd changed anything. Should have done that first.)

If that solves it (I changed settings the last day I was in the office before annual leave) then I can only imagine that the times I get a response from the root NS, the response from the local NS was being sent temporarily to the iPhone. 

If I don't post back, that solved the problem, and thanks again!

---

### Post by SeijiSensei on 2013-07-16
If the original server still has the same IP as the iPhone, then when the phone is active you'll get all sorts of weird results because of the conflicting addresses.

---

