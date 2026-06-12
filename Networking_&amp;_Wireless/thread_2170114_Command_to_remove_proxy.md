---
title: "Command to remove proxy?"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by Jim01 on 2013-08-24
Hey guys,

Probably a stupid question but the only closest thing I could find was this post here:

[http://ubuntuforums.org/showthread.php?t=1253462&highlight=Command+remove+proxy%3F]("http://ubuntuforums.org/showthread.php?t=1253462&highlight=Command+remove+proxy%3F")

Only this guy exported his proxy settings and that isn't quite my issue.

My issue is that I'm playing around with Ubuntu Server 12.04 via Virtual Box, and whilst going from computer to computer I have to run the following commands to get network functionality:

```
cd /etc/udev/rules.d
rm 70-persistent-net.rules
```

For those who don't know if you install ubuntu on 1 computer but then shift to another computer with the same installation you won't have network connectivity, this is because the mac address I believe is written into the file "70-persistent-net.rules", so deleting that file and rebooting ubuntu will regenerate that file with the correct mac address.  Also note you need to be in root to be able to remove that file > sudo -i

Anyway back to my issue:  When I ran those above commands I was at TAFE (the equivalent to college for you americans) and tafe have a proxy, and the problem is whenever I go to install an apt using the usual "apt-get install" commands I get the "cannot resolve 'our tafe proxy' message, how do I remove the proxy now that i'm not using a computer that's attached to that proxy?

[ATTACH=CONFIG]245687[/ATTACH]

Cheer's guys! :)

---

### Post by Jim01 on 2013-08-25
Nevermind I found this thread:

[http://www.linuxforums.org/forum/ubuntu-linux/112090-removing-network-proxy.html]("http://www.linuxforums.org/forum/ubuntu-linux/112090-removing-network-proxy.html")

I actually deleted the file apt.conf and it now works but after looking at this thread I could have just edited the file instead.

---

