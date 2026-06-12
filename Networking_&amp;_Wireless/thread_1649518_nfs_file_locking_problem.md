---
title: "nfs file locking problem"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by n.vanvliet on 2010-12-20
Hi,

I have a ubuntu system running 10.04 LTS (x86).
This system is a nfs client to a Solaris 10 system (x86) that exports the users home directories.
The Solaris 10 system also has a subversion repository.

Ok, so I am logged into the ubuntu machine and from the network share I try to commit something:

[FONT=Fixedsys]svn commit Makefile 
svn: Commit failed (details follow):
svn: Can't get exclusive lock on file '/home/t4/repos/feature/db/txn-current-lock': No locks available
svn: Your commit message was left in a temporary file:
svn:    '/home/t4/nico/Adapt_Crunch/CruncH/feature/trunk/svn-commit.2.tmp'[/FONT]

NOTE: If I do the same at a solaris nfs client it works fine.

The same error can be got if I use the 'flock' command on ubuntu:
[FONT=Fixedsys]flock -e /home/t4/nico/flock.lock -c ls
flock: /home/t4/nico/flock.lock: No locks available
[/FONT]
Is this a known problem for ubuntu as nfs client to Solaris?

I checked on both machines that the relevant services (nfs,lock and stat daemons are running)

Do you have any ideas?
TIA
Nico

---

### Post by earonesty on 2011-05-31
i *had* a similar issue.  all my ubuntu 10 clients refuse to support file locking, but my centos & windows clients work.   

in this case their connecting to a freebsd system running nfs version 3.

no amount of rebooting, reconfiguring or remounting fixed it.

upgrading to "natty" version 11 seemed to work.

---

### Post by n.vanvliet on 2011-06-01
Thanks for your response.

It was some time ago that I had this problem. If I recall correctly it was eventually solved by a reboot of the Solaris server.
I think that there may have been a problem that locks had not been released and a total max. of locks was exceeded.

Anyway everything is working now in the configuration as mentioned in the post.

Regards,
Nico

---

