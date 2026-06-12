---
title: "Wireless network not detected"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by melwaltrip on 2012-12-23
Just loaded Ubuntu 12-10 on an Acer Aspire 5515 laptop. It does not detect my wireless network. How do I get connected. I am NOT an experienced linux user so you will lose me if you get too technical....thanks

I should have mentioned that I use a Verizon Mobile Broadband for my internet connection

---

### Post by TOMBSTONEV2 on 2012-12-23
What is your wireless network adapter model?

Open terminal and type:

```
lspci -nn | grep 0280
```

and post the results.

---

