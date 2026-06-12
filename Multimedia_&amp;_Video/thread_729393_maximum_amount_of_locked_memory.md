---
title: "maximum amount of locked memory"
date: 2008-03-19
forum: Multimedia &amp; Video
---

### Post by johnswb on 2008-03-19
Hello all

When I run Ardour I get the following message:

WARNING: Your system has a limit for maximum amount of locked memory. This might cause Ardour to rum out of memory before your system runs out of memory.

You can view the memory limit with 'ulimit -l', and it is normally controlled by /etc/security/limits.conf

I've looked for an answer to this but could only find info on the subject and not a fix.  I've installed Ubuntu Studio with the following kernel.

uname -r
2.6.22-14-rt
uname -a
Linux meditor 2.6.22-14-rt #1 SMP PREEMPT RT Tue Feb 12 09:57:10 UTC 2008 i686 GNU/Linux

Is it possible to set the limit.conf file to unlimited as far as the memory goes?  If so, what is the setting for that?

Thanks for the help.

---

