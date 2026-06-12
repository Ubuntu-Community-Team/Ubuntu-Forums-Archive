---
title: "Open SSH. Password issue"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by wlraider70 on 2009-05-11
I am trying to get open ssh to open up. 
I keep getting stuck after I type anythink like

$ ssh 10.10.10.2

I get asked for a password but it's never right. 
I have tried all MY passwords is there a set pw command???

---

### Post by dmizer on 2009-05-11
Is the username on 10.10.10.2 different from the username on the system you're trying to ssh from? If so, you'll have to do this:

```
ssh username@10.10.10.2
```

---

### Post by wlraider70 on 2009-05-11
SUCCESS! you my good man are a genius.

---

