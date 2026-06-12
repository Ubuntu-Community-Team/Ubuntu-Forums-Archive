---
title: "How do I remove shorewall???"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Barriehie on 2009-12-15
So I thought I could setup a mail server and that didn't work but in the process I installed shorewall.  Now it's still showing up in the system services and some files do still exist!  How do I completely remove it???

The still existing files are:

```

/etc/default/shorewall
/etc/init.d/shorewall
/etc/logrotate.d/shorewall
/etc/shorewall
/var/lib/shorewall
```

Many thanks,
Barrie

---

### Post by dmizer on 2009-12-15
How did you install shorewall?

---

### Post by Barriehie on 2009-12-15
> **dmizer said:**
> How did you install shorewall?

via synaptic.  Now it says it's not installed so there's nothing to purge!

Barrie

Edit:  I'm thinking maybe install again and try again from the cli with the purge option?

---

### Post by Barriehie on 2009-12-15
> **coolguy123 said:**
> I think the only way to best deal with this situation is a nice, fresh, clean install.  It will completely wipe out those files.

No, my backups already reflect this situation and I'm not going to hose a year + of making this machine like I want over a checkbox!  I'll grep every file in /etc first... :-)

Barrie

---

### Post by Barriehie on 2009-12-15
> **Barriehie said:**
> via synaptic.  Now it says it's not installed so there's nothing to purge!

Barrie

Edit:  I'm thinking maybe install again and try again from the cli with the purge option?

That worked! The only thing left is the /etc/shorewall dir and I can rm that.  Thank you for your time dmizer!

Barrie

---

