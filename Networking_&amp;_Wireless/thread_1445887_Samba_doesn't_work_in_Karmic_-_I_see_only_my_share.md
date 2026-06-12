---
title: "Samba doesn't work in Karmic - I see only my shares, others don't see mine"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by mgol on 2010-04-03
I moved to a different network and I had to add this PPA repository:
[https://launchpad.net/~network-manager/+archive/ppa](https://launchpad.net/~network-manager/+archive/ppa)
so that I could use a PPPoE connection which doesn't work in Karmic otherwise.

Now I see only my shares and others don't see mine; internet works, though. I have the same workgroup as the computer I'm trying to connect with (it has Windows XP on board) but it doesn't seem to help. This Windows XP computer sees other machines in the network, even from different workgroups, so it works OK, it has to be an Ubuntu problem. Restarting didn't help.

Any ideas?

---

### Post by Iowan on 2010-04-04
I presume you've seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To...

---

### Post by mgol on 2010-04-05
The only thing I changed in samba configuration is a workgroup name. I don't think I should touch this file more, especially that in my previous network sharing worked and I haven't changed the configuration since then.

---

