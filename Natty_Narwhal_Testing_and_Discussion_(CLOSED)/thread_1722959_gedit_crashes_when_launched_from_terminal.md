---
title: "gedit crashes when launched from terminal"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Ninwa on 2011-04-06
When I enter 'gedit' into a terminal **only as root** I recieve the following:

```
# gedit

(gedit:18829): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported

**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.5/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)
Aborted (core dumped)
```

This did not occur before upgrading to Natty.

Edit: Additional note - 'sudo gedit' from a regular user does not cause this error.

---

### Post by mörgæs on 2011-04-06
It is not recommended to have a root user:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cariboo on 2011-04-06
> **mörgæs said:**
> It is not recommended to have a root user:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

There many occasions where you need to run as root. For all you know the op could be using sudo -i to get to a root prompt, and running gedit from there.

I just tried it, and unfortunately it didn't crash for me.

---

### Post by Cadeyrn on 2011-04-18
I get this glitch when I try to change gconf from su so that gksu nautilus can have the more advanced permissions menu. It also happens when I run evince (the Document Viewer) through su (but not through gksu), and when I try to open a PDF from gksu nautilus with the Document Viewer, it never pops up.

---

