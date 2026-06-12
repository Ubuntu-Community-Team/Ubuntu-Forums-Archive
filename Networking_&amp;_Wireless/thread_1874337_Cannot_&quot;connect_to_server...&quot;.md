---
title: "Cannot &quot;connect to server...&quot;"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by jperelli on 2011-11-02
Hello!

I'm using ubuntu onieric, 

when I try to create a new bookmark in nautilus using the menu to "connnect to server", I get the error "Can't load the supported server method list. Please check your gvfs installation."

I can't find any information about this error in internet.

Someone knows about this?

Thanks!

---

### Post by efaj on 2011-12-04
Bump, came from Google with the same issue, but I was going to use it for ftp.


Edit: Nowhere did I find info about this... but it only showed up with the window I had opened by root. Nautilus run by user didn't show the error.

---

### Post by FGrose on 2012-06-03
This message will appear when the Nautilus session is launched from  a root user session, such as with gksu or gksudo nautilus, and not when launched from a regular user session.

(Confirmed on Fedora 17 with beesu nautilus.)

---

### Post by edcompsci on 2012-10-14
> **FGrose said:**
> This message will appear when the Nautilus session is launched from  a root user session, such as with gksu or gksudo nautilus, and not when launched from a regular user session.

(Confirmed on Fedora 17 with beesu nautilus.)


I noticed this too. Looking for a way to override it. 

Found this link, but haven't tried it yet.
[http://ubuntuforums.org/showthread.php?t=1960477](http://ubuntuforums.org/showthread.php?t=1960477)

---

