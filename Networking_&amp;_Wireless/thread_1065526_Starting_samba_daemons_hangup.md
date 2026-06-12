---
title: "Starting samba daemons hangup"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by BLTicklemonster on 2009-02-10
Well dooky. I finally got my networking going, and on a reboot, I now get to starting samba daemons, and the machine just stops and nothing happens.

Can I get the system to boot at all? Anyone have any ideas? I won't be able to try anything until tomorrow night probably around 8 pm eastern time US if anyone has any ideas. 

Recovery menu comes up, but nothing there helps. Well, dropping to root shell prompt will, I'm sure, so I'm hoping there's a simple fix someone can turn me on to.
Hardy Heron.

---

### Post by BLTicklemonster on 2009-02-10
I got up early for some reason (buntu senses tingling maybe) and started whacking away.

Finally opened smb.conf, named it to oldsmb.conf, them rm smb.conf and started from recovery. hal failed to initialize of course. Good old hal. Found an old smb.conf~ and opened it, then pasted the contents of it over oldsmb.conf and named it back to smb.conf and rebooted, and it's all fine now.

Jeez.

None of the other machines in the house are on at this time, so no telling if I can network with the xp machines, which I had just resolved Sunday... At least if I run into this again, I know what to do to get back to square one. or two.

---

