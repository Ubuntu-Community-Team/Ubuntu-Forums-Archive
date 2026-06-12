---
title: "Permanent change MTU - Ubuntu 11.04"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by David_UK on 2011-11-26
So I wanted to change my MTU.  No problem, a quick internet search gives:
```
ifconfig
```To view the current values for network interfaces, then:```
sudo ifconfig eth0 mtu 1458
``` to change it (wlan0 for wireless).  All fine.

After reboot - it's defaulted back to the automatic 1500 - oops, this is not permanent.

Internet search = add "mtu 1458" to /etc/network/interfaces.  A problem, this file on my 11.04 has only the loopback listed - no ethernet.  Then I find a post discussing how the mtu is set to auto on network manager - bingo!
[LIST=1]
[*]Click / right-click on network icon
[*]Edit connections
[*]Highlight eth0 or wlan0 as desired
[*]Edit
[*]MTU = automatic.  Click on the tiny "up" arrow.  Enter the MTU you want.
[*]Click save.  Enter admin password.
[/LIST]
Note, the entry for MTU does not actually change in ifconfig until the interface is active - ie network cable plugged in, then it switches from 1500 (default) to whatever you set.

Happy MTUing!

---

### Post by pezplaya on 2012-09-29
I know this thread is old, but is there any way to accomplish with the command line?

---

### Post by David_UK on 2012-09-30
Sorry, I don't know.

---

