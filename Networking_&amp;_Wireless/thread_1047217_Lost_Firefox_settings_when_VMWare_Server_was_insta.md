---
title: "Lost Firefox settings when VMWare Server was installed"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by tbrminsanity on 2009-01-22
I installed VMWare Server yesterday and I noticed that it wiped out my Firefox settings.  I can view them when I sudo into Firefox (which makes me think that my settings are now affiliated with my root account).  The settings still exist under my home directory (.mozilla/firefox/).  

Can someone help me get my settings back.  I don't want to have to sudo into firefox everytime to access my bookmarks (it's dangerous).

---

### Post by tbrminsanity on 2009-01-22
To fix this error I entered the following command into the terminal while Firefox was NOT running:

```
firefox -ProfileManager
```

It grabbed back my profile from the root account.  

Here is the reference where I found out about this fix:

[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

---

