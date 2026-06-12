---
title: "Vaio Ethernet VGN-A190"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by amigammon on 2010-09-10
Hello,

I have never been able to use any network connection on my Vaio except wireless. In many places (hotels, usually) where there are wired connections I get nothing. Whereas with another Vaio I have owned with UbuntuLL also it work just fine. 

I have 1gig RAM and 10.4 installed with all updates. Is there a way to test the ethernet part of the computer?

---

### Post by utilitytrack on 2010-09-11
If answer exactly on your question: 

```
# ethtool --test ethX [online|offline]
```

---

