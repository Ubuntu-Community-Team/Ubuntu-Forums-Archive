---
title: "Can't connect to home network"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by bbichsel on 2010-08-02
I am trying to connect a Vista laptop (wireless) and Ubuntu 10.04 desktop (wired) via a home network to share files on both and a printer on the desktop.  I am relatively new to Ubuntu (and linux), so maybe I am missing something.

I installed Ubuntu on Saturday and when I first logged in it allowed me to connect to local network that is setup on my wireless router.  Followed prompts and connected.  Then I shared folders and printer on desktop and was able to access files from Vista and even move, copy, write, etc.  Could see printer but needed to install drivers for Vista.

Sunday I installed drivers for printer on Vista computer.  Had to restart the laptop to finish install.  Now I can't see the Ubuntu box at all.  Checked desktop and the folders are still shared as before.  I restarted session to make sure no issues with Ubuntu and now I can't connect to the home network.

I have looked at several threads about Samba, but don't know if this is necessary or not since I was connected without it initially.  

Any help wold be greatly appreciated.

---

### Post by marc.verwerft on 2010-08-02
Familiarize yourself with the log files under Ubuntu. All of them can be found under /var/log directory.
Use any editor to view them or use 'System/Adminstration/Log file viewer' to see them all at once.

Most interesting files are 'messages', 'syslog' and daemons.

  > Now I can't see the Ubuntu box at all
Can you ping the ubuntu server? Sometimes it can be something as trivial as a 'disconnected' cable ...

Regards,

Marc

---

### Post by Iowan on 2010-08-02
Which method did you use to share files - there are apparently now three different ways... :-k

---

