---
title: "Openssh-server installation issue"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by psrdotcom on 2011-09-30
When I tried to install openssh-server, I am facing this problem.
```

Setting up openssh-server (1:5.8p1-1ubuntu3) ...
Usage: /etc/init.d/upstart-job {start|stop|restart|force-reload|status}
invoke-rc.d: initscript ssh, action "stop" failed.
dpkg: error processing openssh-server (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server; however:
  Package openssh-server is not configured yet.
dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 openssh-server
 ssh
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please help me to resolve this issue.

Thanks in advance

---

### Post by psrdotcom on 2011-09-30
I have uninstalled the openssh-server and ssh .. 

```

$ sudo apt-get purge ssh
$ sudo apt-get purge openssh-server

```

Then I tried to install the openssh-server again .. I got the same errors

Now, I want to install openssh-server in my system without errors.

Try to resolve this issue.

---

### Post by psrdotcom on 2011-10-03
I tried with my other system .. it was working fine ..

---

### Post by davethewave83 on 2012-01-12
I'm having this error too, I noticed you marked this as solved. Could you post what you did to fix it?

---

