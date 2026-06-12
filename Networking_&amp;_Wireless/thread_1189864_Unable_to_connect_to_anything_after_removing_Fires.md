---
title: "Unable to connect to anything after removing Firestarter Firewall"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by greenmanu on 2009-06-17
Hi All
I have been enjoying Ubuntu for a while now and its about time broak it, and I have by removing Firestarter Firewall. Now I am unable to connect to the Net with my Wireless Card. What should I do folks! apart form kick myself??

---

### Post by sp0nge on 2009-06-17
Well the first thing I would try is to connect wired and see if there is an issue there or not. After we've answered that question, I would first look at the output of:

```
lspci
```

to ensure your wireless driver is recognized and that you're card is active.

Next I would review /etc/network/interfaces and /etc/resolv.conf to see if those were modified by Firestarter- I don't know either way as I've never used it, but this should be a push in the right direction.

---

### Post by greenmanu on 2009-06-17
Many thanks sp0nge!!

---

