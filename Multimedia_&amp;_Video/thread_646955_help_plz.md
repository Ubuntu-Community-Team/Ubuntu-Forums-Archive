---
title: "help plz"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by Ashtesse on 2007-12-21
i'm trying to install emacs but this is the message i get could anybody help what to do
tessema@Bayeh:~$ sudo apt-get install xemacs21-bin
[sudo] password for tessema:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by taurus on 2007-12-21
Do you have synaptic, Add/Remove, or adept running at all?  If you do, you need to shut it down before you run apt-get from a terminal.

Otherwise, post the output of this command from a terminal.

```
ps -A
```

---

