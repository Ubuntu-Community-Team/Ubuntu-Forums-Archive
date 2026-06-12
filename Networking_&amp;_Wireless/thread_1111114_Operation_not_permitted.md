---
title: "Operation not permitted"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by gonzo1948 on 2009-03-30
I am running release 8.04 (hardy).

I am having some problems with opening a socket. I am running my application as root (geteuid() returns 0) and making a system call to socket() and it returns an error of "Operation not permitted"

This is the same error I get if I do not run the app as root, i.e., geteuid does not return 0. The strange part is that this exact same app runs on other Ubuntu systems just fine, that is, if it is run as root, the system calls return non-error. So it appears that there is something different about my system.

So, my question is, what else will cause the socket() call to return with "Operation not permitted" other than not running as root? 

Thanks,

-Andres

---

