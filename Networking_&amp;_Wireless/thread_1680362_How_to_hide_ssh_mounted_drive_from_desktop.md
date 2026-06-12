---
title: "How to hide ssh mounted drive from desktop?"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by beancheese on 2011-02-02
Is there a way to only show mounted USB devices on desktop?
It annoys me a bit, I rarely use my (almost always) connected ssh disk, for other than automated stuff and hopefully soon synchronizing my home :)

Really hope it's possible :-D could be nice if I could make some rules for which disks should be displayed on the Desktop, that would rock! :-D



btw.
I made a some script for automated connection

on server
/etc/cron.hourly/ip_fetch
```
#!/bin/bash

wget www.whatismyip.com/automation/n09230945.asp -O - -q > /home/martin/ip
echo
if diff /home/martin/ip /home/martin/Dropbox/dexolsen/olsen_ip >/dev/null ; the$
else
  cp -f /home/martin/ip /home/martin/Dropbox/dexolsen/olsen_ip
fi

exit 0

```

Yea you guessed it, I have a dynamic ip at home ;) btw I probably could remove the "echo", but it's nice when running it manually.



On the client I have some scripts in /home/martin/.scripts/ssh/

/home/martin/.scripts/sshmount_internet.sh (Shortcut: Ctrl+Super+Alt+I)
```
#!/bin/bash
var1=`grep '^[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}$' /home/mar$
sshfs -o idmap=user martin@$var1:/home/martin ~/fit-pc_home/
exit 0

```

/home/martin/.scripts/sshmount_LAN.sh (Shortcut: Ctrl+Super+Alt+L)
```
#!/bin/bash
sshfs -o idmap=user martin@192.168.2.81:/home/martin ~/fit-pc_home/
exit 0
```

/home/martin/.scripts/ssh_session_internet.sh (Shortcut: Ctrl+Super+I)
```
#!/bin/sh
var1=`grep '^[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}\.[0-9]\{1,3\}$' /home/mar$
gnome-terminal -e "ssh martin@$var1 -X"
exit 0
```

/home/martin/.scripts/ssh_session_LAN.sh (Shortcut: Ctrl+Super+L)
```
#!/bin/sh
gnome-terminal -e "ssh martin@192.168.2.81 -X"
exit 0
```
I've used Ubuntu tweaks for making shortcuts

It all works very well, however feel free to criticize, it helps to develop my scripting/programming skills :-D

Btw.
Been into Ubuntu for 5 months, and I'm really LOVIN' it :eek:
Are there more tasks that could be cool to do on a 27/7 Ubuntu server? :-D

---

