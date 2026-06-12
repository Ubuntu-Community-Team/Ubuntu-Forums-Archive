---
title: "Can never access mythconverg database"
date: 2010-11-09
forum: Mythbuntu
---

### Post by tzoom84 on 2010-11-09
Hi everyone,

Two days ago I installed Mythbuntu 10.10. Both the frontend and backend are on the same machine, and during these attempts mythbackend was running.

I'm trying to manually access the mythconverg database, and any mysql command I put in gives the response:

```
ERROR 1045 (28000): Access denied for user 'XXX'@'localhost' (using password: YES) 
```

I've tried many combinations of "XXX" above (root, mythtv, my user name), and also the password was found using mythtv-setup.

What's strange is even just typing "**mysql**" with *no arguments* gives the same error. Or trying to access a fake database gives the same error.

I've tried both sudo and non-sudo.

Is it a problem with:
a) How I am accessing? 
b) My mythtv setup?
c) The mysql installation?

Thank you.

---

### Post by novellahub on 2010-11-09
Try using the root in the mySQL login and use your user password instead of the one in mythtv-setup.

---

### Post by tzoom84 on 2010-11-09
> **novellahub said:**
> Try using the root in the mySQL login and use your user password instead of the one in mythtv-setup.

Thanks novellahub! That did the trick!

Also, it turned out I wasn't able to log in before using mythtv because I was mixing up a lower case with a capital case. Time for my annual eye exam! :)

---

