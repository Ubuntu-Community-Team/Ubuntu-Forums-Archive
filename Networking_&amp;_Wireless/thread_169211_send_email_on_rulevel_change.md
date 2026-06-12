---
title: "send email on rulevel change"
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by tassoman on 2006-05-02
Hi all,
 I would get an email every time halt / reboot is called from root.

How can I get it?

I was wondering about adding a shell script into rc0.d and rc6.d.
Second idea was including the script into /sbin/halt and /sbin/reboot.

Is this the right way to do it? :-k

---

### Post by geek.de.nz on 2006-05-02
Yes, I can't think of a better way. You could change the halt command to a script and call halt in it, but that wouldn't be as elegant.

---

