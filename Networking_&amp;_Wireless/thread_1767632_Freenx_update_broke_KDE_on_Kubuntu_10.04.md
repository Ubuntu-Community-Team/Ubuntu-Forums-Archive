---
title: "Freenx update broke KDE on Kubuntu 10.04"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by vsteel on 2011-05-25
After a recient update to the freenx libraries KDE on Kubuntu 10.04 stopped working but other desktops like gnome kept running.   The problem wasn't in the normal log files, but it was found in the .xsession-errors file in the user directory on the server.  

After the update NX is trying to start kde with the /usr/bin/startkde4 command which doesn't exist.  Instead make a link from /usr/bin/startkde to the non existent /usr/bin/startkde4 and it will work again.   To do this use the command:

```

sudo ln -s /usr/bin/startkde /usr/bin/startkde4

```All should be good again.

---

### Post by bastafidli on 2011-05-29
Thanks a lot, your solution worked! This affects also Kubuntu 10.10. Maybe you could change the title to reflect that?

---

### Post by vsteel on 2011-05-31
Really glad I could help.  Not sure how many had this problem as I couldn't find any bug reports or others with errors.  Just figured I would throw it up here and hope it helps people.

---

### Post by Njall on 2011-06-02
Your solution also works for Kubuntu 11.04.

---

### Post by vsteel on 2012-09-18
This issue is still in 12.04  The fix above still works and corrects the problem.

---

