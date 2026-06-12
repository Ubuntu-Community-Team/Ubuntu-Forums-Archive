---
title: "How to stop ufw from allowing icmp echoes?"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by josephellengar on 2009-06-29
Thank you.  I'm just a little concerned/security obsessed.

---

### Post by dmizer on 2009-06-30
I believe it should be as simple as:
```
sudo ufw deny icmp
```

Otherwise, you can install the gufw package and configure it via the GUI.

---

### Post by josephellengar on 2009-06-30
> **dmizer said:**
> I believe it should be as simple as:
```
sudo ufw deny icmp
```

Otherwise, you can install the gufw package and configure it via the GUI.

I got this error when I tried that: ERROR: No rules found for application profile

And I have the gui installed but it doesn't mention anything about ping or icmp.  Where would I go for that?

---

### Post by dmizer on 2009-06-30
This is probably what you're looking for then: [http://ubuntuforums.org/showthread.php?t=773485](http://ubuntuforums.org/showthread.php?t=773485)

I really have no idea. I have a router so I don't need to rely on UFW.

---

