---
title: "Asterisk install"
date: 2005-02-07
forum: Networking &amp; Wireless
---

### Post by hungry1 on 2005-02-07
Someone please tell me what URL to put in my /etc/apt/sources.list

Thanks very much,
curt

---

### Post by hungry1 on 2005-02-07
[QUOTE=hungry1]Someone please tell me what URL to put in my /etc/apt/sources.list

Thanks very much,
curt[/QUOTE]

This is to install Asterisk, ( the PBX phone system)
Thanks,
curt

---

### Post by cyberchills on 2005-02-16
I have not been able to find Asterisk either (at least not for warty).  I attmpted to build a CVS snapshot from digium directly and I always error out w/ no termcap support:

configure: error: termcap support not found


I am trying to find out where they are calling for termcap, plan to see if ncurses emul.  will work instead

---

### Post by jesselang on 2007-08-08
You need libncurses5-dev installed.  Then the configure script works fine.  Thanks.

J

---

