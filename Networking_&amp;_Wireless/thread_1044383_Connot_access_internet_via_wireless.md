---
title: "Connot access internet via wireless"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by vancedus on 2009-01-19
Hello,

When I try to access the internet via a wireless connection Firefox never loads the page.  My connection is fine because I can use Synaptic and the update manager but not Firefox. However, Firefox runs perfectly on a wired connection.  This is a recent problem, I was using the wireless as of Thursday.   I am running 8.10 and have an intel PRO/Wireless 4965 AGN. Thanks for the help.

---

### Post by ieee488 on 2009-01-19
Check to see whether in wireless mode whether Firefox starts up in Offline mode.

---

### Post by vancedus on 2009-01-19
Where would I find that out?  Thanks for the help

---

### Post by ieee488 on 2009-01-19
Under File menu in Firefox 3.

---

### Post by vancedus on 2009-01-19
SOLVED

Under the release notes for 8.10 I found that my wireless card causes kernel panics, which also explains the frequent lock ups.  I installed the suggested packages and the problem was solved.  I appreciate the help however.  Thanks

---

