---
title: "SSH Rejects Password"
date: 2010-01-22
forum: Networking &amp; Wireless
---

### Post by kbaum on 2010-01-22
I have OpenSSH running on my Karmic desktop. ssh localhost works fine. But if I try to ssh into it from a different computer on the same network, it rejects my password every time. What could be causing this?

---

### Post by kbaum on 2010-01-23
Bump?

---

### Post by ripeart on 2010-01-23
> **kbaum said:**
> I have OpenSSH running on my Karmic desktop. ssh localhost works fine. But if I try to ssh into it from a different computer on the same network, it rejects my password every time. What could be causing this?

May sound kind of redundant however:

caps lock on?
sure you're connecting to the right box?
have you tried connecting in a terminal like ```
ssh username@IP
```

---

### Post by kbaum on 2010-01-23
Thanks for your response. Caps lock is off, I'm definitely using the right password. The password is all letters and numbers. I've tried connecting from 2 different computers. I'm definitely connecting to the right box, and it responds to ping. I've tried ssh username@IP.

I disabled password login and tried doing it with certificates. ssh localhost used certificates instead of asking for a password, but ssh from a computer on the network still asks for just a password.

Any other ideas?

---

### Post by kbaum on 2010-01-23
Never mind, I figured it out. I had named my machine mythbox, but apparently someone else on my college campus did also, and I was  connecting to their machine, not mine. Thanks!

---

