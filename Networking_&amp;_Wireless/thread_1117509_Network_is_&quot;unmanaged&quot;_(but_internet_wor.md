---
title: "Network is &quot;unmanaged&quot; (but internet works)"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by apanloco on 2009-04-06
Hi, I just switched from Kubuntu 8.10 to Ubuntu 8.10 (installed "ubuntu-desktop") as I read that network-manager had a plugin for PPTP (vpn connections). Now everything is in and most works really well. My problem now is that network-manager does't seem to be in control over the network. It says that My wired network is unmanaged. Adding VPNs and connecting does nothing, like they are stubs, no reaction. There are no entries under the Wired tab. But my internet works perfectly. 

So how do I make network-manager "manage" my wired NIC, and thus enable me to add VPN-connections? Thanks.

---

### Post by Iowan on 2009-04-06
See if [this]("http://ubuntuforums.org/showpost.php?p=6809257&postcount=7") one helps - try the part about:> Managed = true" in the /etc/NetworkManager/nm-system-settings.conf

---

### Post by apanloco on 2009-04-07
Thanks! This took me halfways.

I added managed=true, but when it came back up I could not connect to internet, only local network worked. When editing the network connection I saw that the DNS was empty. When trying to update it I got an error message. I found the bug for this here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/279262)

and the workaround worked.

Thanks a lot for the help,

/a

---

### Post by apanloco on 2009-04-07
Obviously marking the title of your first post with [SOLVED] is not enough to change the thread-title. And non of the Forum Help pages gives an explanatin, so I just keep this unsolved -_-

---

