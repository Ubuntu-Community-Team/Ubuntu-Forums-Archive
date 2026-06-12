---
title: "SSH server running but no startup entry"
date: 2012-05-06
forum: Networking &amp; Wireless
---

### Post by Steve1961 on 2012-05-06
Just a question I'm a little confused about.  My openssh server works fine, I can get into my box without a problem.  However, from what I can see there isn't a startup entry for it (bum, rcconf, etc) in any run level.  So how does it autostart?

---

### Post by Lars Noodén on 2012-05-06
SSH uses [upstart](http://upstart.ubuntu.com/) now.  So you won't find the start up script in /etc/rc0.d - /etc/rc6.d.  You will find it in /etc/init/ssh.conf instead.  The actual sshd configuration is still in /etc/ssh/sshd_config.

---

### Post by Steve1961 on 2012-05-07
That explains it.  Many thanks

---

