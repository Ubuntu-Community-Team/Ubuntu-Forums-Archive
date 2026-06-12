---
title: "restrict root ssh from a particular network"
date: 2013-08-14
forum: Networking &amp; Wireless
---

### Post by chakri78 on 2013-08-14
Hi, 

Is there a way to restrict root ssh from a particular subnet?  ssh or iptable rules? 

thanks,

---

### Post by Lars Noodén on 2013-08-14
Look in the documentation for [sshd_config](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html).  What you are trying to do can be accomplished with the *Match* directive.  In the main body of sshd_config set PermitRootLogin to no.  Then in the match block, select the subnet you want to allow and then set PermitRootLogin to yes.

There's probably another option involving sudo.  It is possible to handcraft a sudo rule to allow just that one function you need and nothing more launched from an unprivileged user account.   That would eliminate the need for remote root login.

---

### Post by chakri78 on 2013-08-15
Perfect solution. Thanks.. 

As you suggested, 

i put PermitRootLogin no

match root@192.168.0.0/16
PermitRootLogin Yes.

All regular users can login from any subnet and root is allowed only from 192.168.x.x

thanks again....

---

