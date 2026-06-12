---
title: "Allow SFTP but deny SSH"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by Holmes89 on 2012-01-27
I need to set up a server that allows SFTP from another server using a planted public key. I would however like to deny this server the ability to SSH. Is this possible without creating a user/ assigning user roles?

---

### Post by sudodus on 2012-01-27
Would it work to make ssh run only for root (who is the owner), that is change permissions for group and others?

```
sudo chmod go-rwx /usr/bin/ssh
```

---

### Post by Lars Noodén on 2012-01-27
> **Holmes89 said:**
> I need to set up a server that allows SFTP from another server using a planted public key. I would however like to deny this server the ability to SSH. Is this possible without creating a user/ assigning user roles?

It's easy to do with the [ForceCommand](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) configuration directive.  The below example allows SFTP for the group 'webmasters' but prohibits SSH for them.  

```

Subsystem sftp internal-sftp

Match Group webmasters
        AllowTCPForwarding no
        X11Forwarding no
        ForceCommand internal-sftp

```

It's very easy to set up, but be sure not to lock yourself out.  
[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#SFTP-only_Accounts](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#SFTP-only_Accounts)

---

