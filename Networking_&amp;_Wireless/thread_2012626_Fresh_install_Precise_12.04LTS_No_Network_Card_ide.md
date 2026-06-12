---
title: "Fresh install Precise 12.04LTS No Network Card identified (RTL8111E)"
date: 2012-06-29
forum: Networking &amp; Wireless
---

### Post by andrewredd on 2012-06-29
I previously had updated to 12.04, but there was a problem with a hard drive not mounting so I decided to do a fresh install. Now the Ethernet network card is not identified.  Please help me fix this.

Since I have no network my also have no copy/paste for the forum, but will convey the info as best I can.  Here are some of the common diagnostics.

```
lspci | grep -i net
```

Return nothing.

```
ifconfig -a
```

only returns an entry for Local Loopback

```
lshw -C network
```

returns nothing.

I attempted to follow the directions in [http://ubuntuforums.org/showthread.php?t=1992200](http://ubuntuforums.org/showthread.php?t=1992200).
But it appears that the module r8168.ko is not installing to /lib/modules. But when I run ```
lsmod
``` after installing I do get that the r8168 module is there but not being used. After restart it disappears.

Now I'm stuck where to go next.

---

