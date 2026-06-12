---
title: "nm-applet vanished, can't get it back"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by Fallingwater on 2012-09-10
I'm attempting to fix a Ubuntu install belonging to a friend (10.10 preinstalled on EeePC). From her recount the network applet vanished first, then she tried tinkering with the taskbar to bring it back and inadvertently removed the whole notification area. I added it back, but it's still missing the network applet icon.

I googled and read various threads concerning similar problems, but no fix has yet worked, even some that have solved the issue for other users.

Here are some facts:

- normally nm-applet is running, but not appearing
- if I kill it and run it again in the terminal, it says the following:
[html]** Message: applet now removed from the notification area
** (nm-applet:1906): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1906): DEBUG: old state indicates that this was not a disconnect 0[/html]- running it with "nm-applet --sm-disable" makes no difference
- running it as superuser makes no difference
- adding another notification area only adds another set of the icons I already have there
- /etc/network/interfaces only has the two lines it's supposed to have ("auto lo", "iface lo inet loopback")
- restarting network-manager does not work, but does cause the nm-applet terminal to output more lines:
[html]** Message: NM disappeared
** (nm-applet:1906): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1906): DEBUG: old state indicates that this was not a disconnect 0
** Message: NM appeared[/html]- I can't do a network reinstall of network-manager, because the computer can't connect to the internet until I fix this problem

Any ideas?

---

### Post by iponeverything on 2012-09-10
open a terminal and run:

```

nm-applet&
disown %1

```

---

### Post by westie457 on 2012-09-10
The answer you are looking for is here in post #2

[http://ubuntuforums.org/showthread.php?t=1652235](http://ubuntuforums.org/showthread.php?t=1652235)

It should work.

---

### Post by Fallingwater on 2012-09-10
> **westie457 said:**
> The answer you are looking for is here in post #2

[http://ubuntuforums.org/showthread.php?t=1652235](http://ubuntuforums.org/showthread.php?t=1652235)

It should work.
This worked beautifully. Thanks!

---

