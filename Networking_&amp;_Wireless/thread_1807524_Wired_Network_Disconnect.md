---
title: "Wired Network Disconnect"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by Surreall on 2011-07-19
Hi all,

I am a complete noob with Linux, but i am trying

Here is my situation...i installed linux at home on my laptop (dv2000, hp). Because i was having problems connecting to the internet through wireless. And wired at friends houses

So installed linux. Wireless took me a while but finally got that working. Now the problem i have is that wired is not working apart from at home. Any other router apart from mine it cannot connect to. And i have no idea why?

Are there any suggestions?

Rgds

---

### Post by jmoorse on 2011-07-19
Just to make sure I understand: Wireless works fine, wired only works at home?

Please post the output of:

```

ifconfig -a
cat /etc/network/interfaces

```

---

### Post by 2F4U on 2011-07-19
Is the wired connection set to connect automatically? In order to verify, open your network connections, edit the wired connection and check that "connect automatically" is checked.

---

