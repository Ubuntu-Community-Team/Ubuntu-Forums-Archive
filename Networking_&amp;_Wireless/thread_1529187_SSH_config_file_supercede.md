---
title: "SSH config file supercede?"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by oomar on 2010-07-11
Hey so this is just a quick question.

I added an alias for SSH in ~/.ssh/config. 

The standard.... Host, Hostname, and Port.


Well I know that the sshd config is somewhere else and that just kind of got me worried if this would somehow freakishly wipe out settings for ssh. I don't really know why. Just thought I'd ask if creating the config file would mess something up. Idk. yay paranoia.

---

### Post by Brandon Williams on 2010-07-12
~/.ssh/config does not override anything from the sshd config. It is for overriding elements of the system-wide /etc/ssh/ssh_config file, which impacts the ssh client, not the ssh server.

---

