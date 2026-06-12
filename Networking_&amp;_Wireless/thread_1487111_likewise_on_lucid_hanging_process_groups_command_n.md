---
title: "likewise on lucid hanging process groups command not respondig"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by root75 on 2010-05-18
Hi

I have configure likewise on lucid.
I am trying to log in with an AD user , and the login process is pending on the groups command, if I hit ctrl+c , I can have the bash prompt.

I have make a strace of the process , and it seems that the groups parse all the group value returned by the AD, but our AD has lot of data.
How can avoid this ?
How the groups command can respond in a acceptable delay ?




root 23433 684 0 15:57 ? 00:00:00 sshd: XXXX [priv]
54560718 23439 23433 0 15:57 ? 00:00:00 sshd: XXXX@pts/12
54560718 23440 23439 0 15:57 pts/12 00:00:00 -bash
54560718 23446 23440 0 15:57 pts/12 00:00:00 -bash
54560718 23447 23446 35 15:57 pts/12 00:00:06 groups

---

