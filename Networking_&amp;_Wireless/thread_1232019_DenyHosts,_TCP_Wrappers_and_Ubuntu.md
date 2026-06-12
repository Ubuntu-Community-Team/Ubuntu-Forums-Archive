---
title: "DenyHosts, TCP Wrappers and Ubuntu?"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by iandol on 2009-08-05
Hi,

I installed the fantastic Denyhosts to keep brute-force attacks on my SSHd under control. One requirement is that the sshd is compiled with TCP wrappers enabled, which I think ubuntu's package is, as tested with:

```
 ldd /usr/sbin/sshd | grep libwrap
```

However one weird issue is that when i follow the guide to see if TCP wrappers is working:

[http://denyhosts.sourceforge.net/ssh_config.html](http://denyhosts.sourceforge.net/ssh_config.html)

where hosts.deny has "sshd: 127.0.0.1" added and one tries to "ssh localhost", I am not refused permission as expected. Does anyone know why ubuntu is not blocking/using that rule?

---

