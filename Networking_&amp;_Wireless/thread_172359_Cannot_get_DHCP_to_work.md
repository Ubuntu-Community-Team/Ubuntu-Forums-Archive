---
title: "Cannot get DHCP to work"
date: 2006-05-08
forum: Networking &amp; Wireless
---

### Post by VoiceOvGod on 2006-05-08
Just recently had to reinstall my copy of Breezy.

Prior to the reinstall, DHCP worked fine.

Went through and updated everything.

Now I can't use DHCP. My network connection attempts to activate, says it is active, then deactivates again.

The local settings on the network (mixed network using XP and Breezy) are set up for DHCP.

I couldn't find anything similar to this in the forums, but if there is another article on this, please send me the link.

---

### Post by Iowan on 2006-05-09
Thought I'd seen something similar posted, but can't find it...
Grasping at straws, but I wonder if the DHCP server has "remembered" something about this box (MAC address) that needs to be flushed.

---

### Post by matthewstory on 2006-05-09
flushing the DHCP tables will be different on each DHCP server, you could just restart the DHCP server if you don't mind your network being down for about a minute.  Also look at your /etc/network/interfaces file, assuming you're not connected wirelessly it should look like this for eth0:

auto eth0
iface eth0 inet dhcp

If it is wireless you'll need some more specific commands, I can help with that also if you need.

---

