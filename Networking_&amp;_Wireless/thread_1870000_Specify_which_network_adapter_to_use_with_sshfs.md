---
title: "Specify which network adapter to use with sshfs?"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by atm999 on 2011-10-26
Hi guys,

I'm running two headless ubuntu servers which I am connecting with sshfs. One of the machines has two network adapters (interface cards). When connecting from the two-adapter machine to the single-adapter one, is it possible to specify which adapter I want to use for the outgoing sshfs connection, and if so how? I know that if I were to connect from the single-adapter machine to the two-adapter machine this would be easy, but for reasons that I won't go into this isn't possible. Thanks for your help!

---

### Post by Lars Noodén on 2011-10-26
In ssh it should be -o BindAddress to bind to an outgoing address.  

For ssh-based utilities there is usually the possibility to pass [options](http://manpages.ubuntu.com/manpages/oneiric/en/man5/ssh_config.5.html) from the utility to ssh.  I would look in detail at the man page for sshfs and see if -o does anything like that.

---

### Post by atm999 on 2011-10-26
sshfs has the syntax "sshfs [EMAIL="user@remotehost.com"]user@remotehost.com[/EMAIL] /mount/point -o option=setting". For example, "-o cache_timeout=20" I've tried using "-o bind_address=x.x.x.x" (putting in my real IP address) but without any luck (it give an "unknown option" error). The man page has no obvious way to pass ssh options directly. Thanks for trying though. Do you (or anyone else) have other ideas?

Edit: scratch that, apparently the correct setting is "-o BindAddress=x.x.x.x" I didn't capitalize the "A" the first time. Thanks for your help!

---

