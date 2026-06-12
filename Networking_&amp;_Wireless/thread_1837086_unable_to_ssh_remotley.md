---
title: "unable to ssh remotley"
date: 2011-09-01
forum: Networking &amp; Wireless
---

### Post by corkscrew on 2011-09-01
I have a network running behind an ADSL router, all machines are running hardy heron.

I wish to access one of the laptops using ssh when I am away from home.
( I can gain access to my network because I have a Dynamic DNS service).

I have set up the laptop with ssh server and generated RSA private and public keys and have tested accessing the laptop from 2 different boxes in the network and works fine without entering any passwords.

If however I try to access the laptop from outside through DNS service it asks for password I enter the username password no success it asks 3 times them gives me this message ```
Permission denied (publickey,keyboard-interactive)
```

---

### Post by corkscrew on 2011-09-02
fixed the issue for myself might be of help to some people, I was accessing 2 machines behind my router so I had to put one ssh server on a different port

---

