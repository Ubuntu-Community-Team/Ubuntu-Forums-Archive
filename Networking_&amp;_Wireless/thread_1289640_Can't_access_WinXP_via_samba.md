---
title: "Can't access WinXP via samba"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by gwpritch on 2009-10-12
I am trying to network two boxes together. One has winxp the other runs jaunty. I have set up as described in a how to I found on this forum. Now I can access ubuntu from the xp box but I can't access xp from ubuntu.
When I click on network in nautilus I get Windows networks. From there I can get to the work group and from there can see the xp box but when I click on it, after a pause I get a dialog saying cannot mount shares. Any help would be appreciated.

---

### Post by Iowan on 2009-10-12
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To?

---

### Post by gwpritch on 2009-10-12
Thanks.  I worked my way thru that how-to but now joy. However, I found a related thread that set me right.

When editing /etc/nsswitch.conf the line reading:

```
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
```

should be edited to:

```
hosts:          files [COLOR="Red"]wins[/COLOR] mdns4_minimal [NOTFOUND=return] dns mdns4
```

not:

```
hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="red"]wins[/COLOR] dns mdns4
```

as suggested in the first how-to. Thanks for pointing me in the right direction.

---

### Post by gwpritch on 2009-10-12
Damn...thought I had it then I rebooted and I'm back to square one. Actually square -1 because now I can't even see the workgroup.:(

---

