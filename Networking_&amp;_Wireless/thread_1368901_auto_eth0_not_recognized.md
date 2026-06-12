---
title: "auto eth0 not recognized"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by som1special2 on 2009-12-31
I have a gateway LT20 that does not recognize when an ethernet cord is plugged in. Wireless works, but no wired. I use Mint 7, how can I fix this?

---

### Post by shairozan on 2009-12-31
Hey there, 

First thing is we need to see if the distro is recognizing the card at all. Post the output from the following terminal command:

```

ifconfig -a
```

Then post the output from this command
```

lspci
```

If the machine already shows eth0 in ifconfig, then it's already registering the card, and the issue either has something to do with a bad cable, a bad NIC interface, or a bad switchport for whatever you're plugged into.

---

