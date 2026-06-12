---
title: "Can't get XP &amp; Ubuntu to play nice"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by Throne777 on 2010-11-08
I'm running Ubuntu 10.10 and my housemate is running Windows XP. I'm trying to make my music folder accessible to him via our network, but I can't get the two to recognise each other.
I have the folder sharing options set as in the picture (samba is installed, etc). Adding a new network place on Windows XP and putting the path as:
\\throne-home\music (I tried a few other combinations to no avail)
and Windows refused to acknowledge it. 
Any suggestions?

(If it makes any difference, I'm running Ubuntu x64)

---

### Post by zexelon on 2010-11-08
Quick thing, when you type in \\throne-home\music on the XP machine does it ask for a username and password or does it just time out? 

If it is timing out you might want to try the direct IP of the machine, i.e. \\xxx.xxx.xxx.xxx\music, where the x's are the linux machines ip address, found by the following:

```
#ifconfig | grep "inet addr"
``` 

Hope this helps, windows is notoriously unreliable at resolving host names on a home network, it usually works best to use the direct IP to the machine.

---

### Post by Throne777 on 2010-11-08
> **zexelon said:**
> Quick thing, when you type in \\throne-home\music on the XP machine does it ask for a username and password or does it just time out? 

If it is timing out you might want to try the direct IP of the machine, i.e. \\xxx.xxx.xxx.xxx\music, where the x's are the linux machines ip address, found by the following:

```
#ifconfig | grep "inet addr"
``` 

Hope this helps, windows is notoriously unreliable at resolving host names on a home network, it usually works best to use the direct IP to the machine.

Ah, direct IP worked. Thanks for that.

---

