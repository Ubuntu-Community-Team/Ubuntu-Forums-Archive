---
title: "Nforce2 100BaseT NIC Running at 10BaseT?"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by twokatmew on 2006-01-06
Hello,

I installed Ubuntu 5.1 a few days ago and have been starting the process of learning Linux.  Adding another machine to my LAN meant I needed a new switch in my office, however, so I picked up a Netgear GS108 8-port gigabit switch.  The switch shows my Ubuntu box (which has a 100MBps NIC) is running at only 10MBps.  This machine dual boots WinXP Pro SP2, and I have the same NIC configured to force 100/half duplex.  When I boot Windows, the switch shows it's running at 100MBps.  

I run NetPerSec on Windows to watch the speed of my machines, but I don't know of a tool for this on Linux.  So I have two questions:  What tool can I install/use to watch transfer speeds under Ubuntu?  And second, how can I configure the speed I want my NIC to run at in Ubuntu?

Thanks!

---

### Post by Lambert on 2006-01-06
from terminal

```
ethtool ethx
``` 
shows information about the nic. (replace ethx with the name of your nics interface eth0, eth1, etc...)

to set the speed is something like

```
ethtool -s eth0 speed 100
``` to change speed
```
ethtool -s eth0 duplex full
``` to change duplex

Not sure if these change at each boot or are permanent.

you can read more on the man page.[I] man ethtool

[/I]Not sure about an app that measures network performance. Looked at a couple but didn't try them or remember what they were.

---

### Post by twokatmew on 2006-01-07
Thanks for the info, Lambert!  :-)  I found that ethtool only works if I preface it with "sudo," no prob.  According to the man page for ethtool, you can use it to view and change settings (which get saved).  Unfortunately for some reason, I'm unable to save changes, even using sudo.  But I've been able to confirm that my adapter is running at 100Mbps.  According to the doc on my Netgear switch, the solid green light I'm seeing indicates a 10Mbps connection.  But my testing has shown there's a bit more to their simplistic doc.  That green light actually indicates that autoneg is on.  I'd prefer to turn that off, but no biggie.

Anyway, thanks for your help.  I'd still like to find a transfer speed monitoring tool, so if anyone else has one or more to recommend, I'd be interested in a pointer to 'em.

Thanks!  :-)

---

