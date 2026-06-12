---
title: "Freezes after long periods of non-use"
date: 2011-01-02
forum: Mythbuntu
---

### Post by barrylumpkin on 2011-01-02
MythTV is working well except for one thing... if I don't use it for several days, when I turn the monitor on, the screen is frozen. Neither the Microsoft remote nor the keyboard is responsive. I have to reboot the system. Then everything's great again.

Apparently, when the system freezes, no recordings are made.

I've done all the MythTV updates whenever prompted. I have zero problems unless I go a few days without watching TV. Strange.

Any ideas?

---

### Post by newlinux on 2011-01-02
might not be a myth problem but a system problem. Hard to tell from the info you've given. Take a look at your myth logs and probably /var/log/syslog and /var/log/messages from the days/times when it froze to see if there are any clues.

---

### Post by barrylumpkin on 2011-01-02
> Take a look at your myth logs and probably /var/log/syslog and /var/log/messages

Being a beginner... I don't know how to do this. Sorry.

---

### Post by newlinux on 2011-01-03
myth frontend and backend logs are just files typically located in the directory.

/var/log/mythtv


you can use tail (to look from the end of the file back) or more (to look from the beginning of the file forward) to view the file from command line

e.g. ```
more /var/log/syslog
``` or ```
tail /var/log/mythtv/mythbackend.log
``` - or if you are uncomfortable with the command line you can just open up the files with a regular text editor of your choice.

---

