---
title: "trouble with playing dvd"
date: 2009-02-22
forum: Multimedia Software
---

### Post by wolfman1221 on 2009-02-22
i am trying to install medibuntu, and i have run into an issue. i followed the directions on this link '' [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)'', and this was the message i recieved in my terminal.

'' sudo apt-get install libdvdcss2
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?''

If anyone could help me, it would be much appreciated.

---

### Post by orethrius on 2009-02-22
Either your system is already updating packages (only one such process can run at a time), or some updater has crashed and left its lockfile in place.

Case 1, updates are running: wait until they finish, then try again.
Case 2, updates crashed at some point: hold Alt, hit F2, and type the following, followed by Enter (the ' is a single-quote, not a backtick).
```
xterm -e 'gksudo rm /var/lib/dpkg/lock'
```

Be VERY CAREFUL to enter the above code as shown.  Any form of **sudo rm** is a ROOT PRIVILEGE DELETE COMMAND, and can be dangerous when handled without care.

---

