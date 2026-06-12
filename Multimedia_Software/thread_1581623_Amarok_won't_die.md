---
title: "Amarok won't die"
date: 2010-09-25
forum: Multimedia Software
---

### Post by backspace on 2010-09-25
Hi,

Right now at my wits end after upgrade to Ubuntu 10.04 from 9.01 and a battle to get Amarok to play my music files. 

I now have Amarok playing my music files but once I quit, Amarok doesn't open again. It wouldn't even open from the icon on the panel. 

After a restart, Amarok would open again.

I check 'System Monitor' after quitting and Amarok is still there "sleeping". Once I kill the process in 'System Monitor' I can open it from the 'Applications' drop down menu.

Why doesn't Amarok quit properly? . . . and what is that KDE wallet all about?

Much appreciate any help on this one.

---

### Post by mc4man on 2010-09-25
You could try this - (you may need to remove amarok then re-install it, maybe not
```
sudo apt-get install mysql-server-core-5.1
```

old, related bug concerning music collection, an unclean shutdown was also seen.
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269)
[http://ubuntuforums.org/showthread.php?t=1518936](http://ubuntuforums.org/showthread.php?t=1518936)

don't know much about the wallet deal, I just click thru it once and it thankfully never shows up again

---

### Post by backspace on 2010-09-25
Thanks mac4man . . . that fixed it :))

Worked a charm, no need to reinstall.

. . . brilliant.

---

