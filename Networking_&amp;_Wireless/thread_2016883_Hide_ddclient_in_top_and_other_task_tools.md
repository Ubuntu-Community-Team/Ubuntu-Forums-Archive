---
title: "Hide ddclient in top and other task tools"
date: 2012-07-04
forum: Networking &amp; Wireless
---

### Post by sakalonys on 2012-07-04
Hi guys,
i want to remote watch my homestation, when i&#7743; at work.
the problem is my half static ip, cause of that i need smth like sshd.
but everytime my brother takes a look at top, he kills the daemon.
is there a way to run the process hidden by default at startup ?

is it the easiest way to spread my dynamic-ip? 

thanks

---

### Post by SeijiSensei on 2012-07-04
How about, as an alternative, you ask your brother to stop doing that?  Or, another alternative, you remove his root privileges so he can't do that?

---

### Post by sakalonys on 2012-07-05
thanks for ur answer , that would a possibility.
is there a way to deny his control for one process ? what a question its linux the user permission OS... :-)
but it would be nice, to tell me if u know, before i start googlin again ...

---

### Post by SeijiSensei on 2012-07-05
Nothing can keep someone from killing any process if they have root privileges.

It's possible to start daemons as an ordinary user and thus keep others from killing them (again assuming they cannot become root), but only root can bind a process to a port below 1024.  I don't know if it's possible for an ordinary user to start an instance of sshd bound to a high port, but if so, that's one approach.  Still as long as your brother has root privileges there's nothing you can do to stop him from running roughshod over the entire system.

---

### Post by Ashtechsmith on 2012-07-05
Thanks for the help.....
Now my problem is solved out.
thank you

---

