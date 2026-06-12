---
title: "Disable Network Notification Ballons"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by jwsicomputing on 2012-03-18
Hello,

I am using my Ubuntu 11.10 machine as a dhcp server and all the time I am confronted with balloons saying connection established and connection disconnected.

Is there a way to disable these balloon notifications?

Many Thanks,
James

---

### Post by DeMus on 2012-03-18
See here where they have the same problem:
[http://ubuntuforums.org/showthread.php?t=982097]("http://ubuntuforums.org/showthread.php?t=982097")

---

### Post by jwsicomputing on 2012-03-18
thanks

you just need to use the same terminal command except like this:

sudo chmod -x /usr/lib/notify-osd/notify-osd
pkill notify-osd

James

---

### Post by jjjjeremy on 2012-03-25
No need to run any commands, there are checkboxes in gconf-editor for it.

apps>nm-applet

It's in the nm-applet parent folder, not the ignore-ca-cert child folder.

---

