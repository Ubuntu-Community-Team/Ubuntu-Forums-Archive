---
title: "Have to join the domain on each boot"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by alkisx on 2009-04-07
Setting up a new computer, I joined successfully on the domain of the network:

net rpc join -w DOMAIN -S SERVERNAME -U root

I get the message: 'joined the domain DOMAIN'

after the above command the nework is available with all computers.

But on the next reboot, nothing is available, unless I type the same command for joining the network. The samba settings are properly set for the domain.

Anyone knows how to keep the joining on next reboot?

---

