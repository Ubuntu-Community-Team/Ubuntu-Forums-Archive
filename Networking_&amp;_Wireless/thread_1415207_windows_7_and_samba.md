---
title: "windows 7 and samba"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by koukos on 2010-02-24
When i try to copy files from my samba server (Ubuntu 9.10) to my windows seven media center, the speed is extremely slow. So slow that is better to download 100mb file from the internet, than from my lan. And on my lan, every card and switch is at 1000 mbps speeds on cat5 cables. And from XP or other linux machines, i dont have any problem. Any idea?

---

### Post by ojobson on 2010-03-14
This seems to be a common problem - I am trying to solve it too.

Writing to the samba share on my Ubuntu 9.10 server is around 35 to 50 MBps depending on the client. Reading from the server using samba is about 7 MBps on both Win and OS X clients (which can talk to each other at about 45 MBps over samba).

The server can handle reads through appletalk at 45MBps - so I don't know why I am only getting 7MBps over samba...

very confused.

---

