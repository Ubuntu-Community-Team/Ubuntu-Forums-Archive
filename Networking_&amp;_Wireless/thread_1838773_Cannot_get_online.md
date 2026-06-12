---
title: "Cannot get online"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by dondada on 2011-09-04
This has been driving me nuts! My Ubuntu Natty install cannot get online. I'm on my network and can access my router as well as my other networked PCs but just cannot get online. My other PCs are online. These are a mix of Win and Ubuntu, wired and wireless.

The PC in question has been rebooted numerous times. I can ping within my LAN but cannot reach anything outside. I am also using a static IP.

---

### Post by stephenconnolly on 2011-09-04
Hey, I'm having exactly the same problem, still waiting on a solution. My post is here, so might be worth keeping an eye this thread as well:

[http://ubuntuforums.org/showthread.php?t=1838740](http://ubuntuforums.org/showthread.php?t=1838740)

---

### Post by dondada on 2011-09-04
Just fixed it. I was having issues with my Network Manager earlier which was giving me an error indicating 'no valid connections'. As describe [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/305606"), I went into 

> cat /etc/NetworkManager/nm-system-settings.conf

and changed the 'managed' setting to 'true'.

This fixed my Network Manager issue but I was still unable to get online. I also noticed that Network Manager now had 'ifupdown (eth0)' as the selected adapter. Instead of this, I clicked on the 'Auto eth0' adapter option and this brought me back online. This is completely odd to me, but whatever, it worked.

---

### Post by stephenconnolly on 2011-09-04
Dondada, thanks for the post. I had exactly the same problem, I'm back online now.

---

