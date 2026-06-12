---
title: "SAMBA PDC Authentication (9.10)"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by AlexDBall on 2009-12-12
Dear all,

This is my first post to the forum and thanks for the great support you have provided me in many topics!

I would like to know how to configure my system (Ubuntu 9.10) to authenticate to a SAMBA PDC.

I have found and followed this thread ([http://ubuntuforums.org/showthread.php?t=5409](http://ubuntuforums.org/showthread.php?t=5409)), but it does not seem to work in 9.10.

The machine can join the domain, a machine account is created on server but no domain accounts can login in either ssh, terminal or gdm. 
Even local accounts cannot login! I have to boot into recovery mode and restore the modified files (listed in the attached post)

I beleive that there might be something wrong/changed in the configuration of the files located /etc/pam.d/ for 9.10 due to the fact that the attached post is a bit old.
Please note that Windows machines can join the domain and login   successfully.(XP/2003)


Thanks for your time.

Alex

---

### Post by AlexDBall on 2009-12-15
I've managed to figure it out. Tested it on two computers and it works!

However i cannot seem to log on when there is no network (winbind cache time = 10 from smb.conf) not working?

If anyone is interested let me know and i'll post all config files.

---

### Post by rlillard on 2010-01-12
I believe I have the same problem you did.  I am trying to make my karmic box behave as a member server in a samba (NT) domain.  I have joined the domain, wbinfo and smbtree work, but other machines in the domain cannot access anything on my new karmic system.  I can browse other machines.  I too believe it is a pam problem.  What was your fix??

---

