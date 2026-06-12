---
title: "x11vnc killed after login"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by sparks13 on 2009-09-14
I have been fighting the everlasting battle of trying to get VNC to work without requiring a user to login locally first. I found this tutorial ([http://www.homecncfun.com/blog/2009/05/20/how-to-setup-a-full-graphic-login-via-vnc-on-ubuntu-jaunty/](http://www.homecncfun.com/blog/2009/05/20/how-to-setup-a-full-graphic-login-via-vnc-on-ubuntu-jaunty/)) along the way. On system boot, I could connect using a vnc client and enter username/password. Then as the system logged in, the connection would drop. Trying to reconnect gives an error. If I SSH in, and enter this command:
```
x11vnc -nopw -auth /var/lib/gdm/:0.Xauth -display :0 -noxfixes -bg -sb 11 -forever

```
I can reconnect and everything runs just fine.

I found this thread ([http://ubuntuforums.org/showthread.php?t=321918](http://ubuntuforums.org/showthread.php?t=321918)) which sounds exactly like my problem, but there was no solution and I couldn't post there. Any help on this matter would be much appreciated. Please note I am currently running on 9.04 which seems to be where things got tricky again from all the reading I have been doing.

---

### Post by krunge on 2009-09-14
You've put```
KillInitClients=false
``` in gdm.conf, gdm-custom.conf, and etc.?

BTW one way to see if the file(s) you've edited are actually read by gdm is to move the file aside, restart gdm and look for differences (e.g. appearance and logfiles)

---

