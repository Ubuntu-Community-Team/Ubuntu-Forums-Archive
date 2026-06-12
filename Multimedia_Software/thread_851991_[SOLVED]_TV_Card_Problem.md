---
title: "[SOLVED] TV Card Problem?"
date: 2008-07-07
forum: Multimedia Software
---

### Post by rijalul on 2008-07-07
I have use GADMEI tvcard to capture TV show.
When I migrate into ubuntu, my tv-card doesn't recognized by ubuntu. How can I configure my tv-card?
Sorry, I'm newbie in ubuntu.

Thx b4. :)

---

### Post by eldragon on 2008-07-07
> **rijalul said:**
> I have use GADMEI tvcard to capture TV show.
When I migrate into ubuntu, my tv-card doesn't recognized by ubuntu. How can I configure my tv-card?
Sorry, I'm newbie in ubuntu.

Thx b4. :)

```

lspci

```

even though i will not be of much help probably, the output of that command will help others help you :D

---

### Post by secondstage on 2008-07-07
Try...
```
sudo apt-get install tvtime
```
Once installed, it should be found in Applications > Sound & Video. You can left-click to see what input your on, and what time it is. Right-click to get into settings. Change the input if your not getting any signal. 

--secondstage

---

