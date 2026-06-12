---
title: "automount nfs via ldap, networkwait"
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by oliver lee on 2013-04-20
Hello all,

I've set up an LDAP server which I use for user authentication and automounts on two clients, one is a laptop running ubuntu 12.10 and the other is a desktop running Debian 6.0.7. The server is a headless Debian 6.0.7. 

Obviously I'm affected by [733914]("https://bugs.launchpad.net/ubuntu/+source/autofs5/+bug/733914") and the related [40189]("https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/40189"), [213574]("https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/213574"). If you're not familiar, autofs doesn't wait for network-manager to bring up any networks, so when it attempts to contact the LDAP server to retrieve mount information it fails. The inconvenient solution is to manually start autofs after networks have been brought up, or remove network manager (a pain in the case of a laptop :( )

The automounts are NFS mounts, although I don't think that's actually relevant. If I set up the mounts manually in fstab then they mount correctly, and I'm pretty sure the  bug still applies with non NFS mounts because autofs fails before getting any information about the mounts (at this point it doesn't even know they are NFS)

This bug has been present for years (since 2006 in the case of [40189]("https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/40189")) unless I've missed something.

My real question is: some RedHat users have reported fixing the problem by adding [COLOR=#000000]NETWORKWAIT=yes in /etc/sysconfig/network, but neither debian nor ubuntu have this directory. Is there an equivalent option I can use in ubuntu?

Thanks in advance[/COLOR]

---

### Post by oliver lee on 2013-04-26
Updated to 13.04 today and no fix

Does anyone have any suggestions?

---

### Post by oliver lee on 2013-04-28
Setting 
start on (starting autofs)
in /etc/init/network-manager.conf does not fix the problem. Autofs will start after network-manager, but before it actualy brings up any of the networks.

---

