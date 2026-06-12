---
title: "Visulizations crash"
date: 2013-09-15
forum: Multimedia Software
---

### Post by bobblues on 2013-09-15
I am using ubuntu 12.10 with VLC media player and Project M visulizations. I am using music from my hard drive. At times the program freezes and I must reboot. I feel this is a problem with Project M and not VLC or ubuntu. I down loaded Project M from Ubuntu software center. The crashes are iratic sometimes after 10 min. and sometimes after over an hour. Is there a way to check the log file for the bad file and remove it?

---

### Post by tgalati4 on 2013-09-15
Look in /var/log/syslog for any obvious clues.  It's possible that your graphics chip is overheating and causing a sudden lock-up.  Do you have any temperature sensors enabled?  Install *htop* and monitor that in a separate window.  If your CPU is running less than 30% throughout a music session, then it's probably a GPU issue.

---

