---
title: "Packard Bell TN65"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by sampsd on 2011-03-27
I am finding it difficult trying to connect to wireless using my laptop. It is saying that wireless connections are disabled. Wired connections work fine but it would be much easier if I could have a wireless connection.

---

### Post by nickleboyblue on 2011-03-27
What wireless card is in your laptop?  Without knowing that, nobody will ever be able to help you.

First, type the following in a terminal (accessed int the Applications->Accessories->terminal menu):

```
lspci | grep Wireless
```

That should show you the entry for your wireless card.

Post back here with that entry, AND search for it online.  Chances are that someone else has had the same problem as you, and that they already found a solution to their problem.  If you find a solution on your own, post the link back here just in case someone else has the same problem.

---

