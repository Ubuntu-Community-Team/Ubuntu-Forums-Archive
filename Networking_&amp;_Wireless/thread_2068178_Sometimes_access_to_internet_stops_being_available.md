---
title: "Sometimes access to internet stops being available"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by 3Nex on 2012-10-08
I haven't been able to figure out what causes the problem. Sometimes i think it's because i have so many "internet applications" open (like firefox + pidgin + transmission + skype + teamviewer...). All of the sudden, all internet access becomes unavailable. I cannot access any internet services; If i try to ping a server, it says "unknown host"; Pinging my router works fine.

After reboot, it's okay again.

But it's not because of the IP change for sure, because this problem can happen any number of times during the day and it doesn't start working again no matter how long i wait (until i reboot). 

Sometimes i try to narrow down to see if it's one specific application, but no obvious pattern is to be seen. Altho that thought seems to be on the right track, because when i only use Firefox, it never-ever happens.

Also, it doesn't happen immediately after i open an application (obviously, otherwise i'd be able to figure out which application it was). Today it happened after having transmission opened for like 20 minutes, last time it happened was like a month ago.

Restarting /etc/init.d/networking does not help, rebooting the computer does. What can i try that would narrow down on the cause of the problem? Is there some log file where i could check for errors or something? 

I'm using Ubuntu 10.10 and Gnome 2.30.2

---

### Post by TheFu on 2012-10-08
What do the log files show?

I doubt the issue is actually related to an application, but 
it could be related to having the wrong network driver or 
it could be a hardware issue that happens only with the network chip gets hot or
it could be that your router isn't tuned for so many active connections, so it drops some or
it could be that your router is overheating and dropping connection or 
it could be that some firewall rule is auto-engaging after a certain number of suspect packets are seen or 
Or it could be one or thousands of other things.....

Until you have facts from the log files, we are only guessing.

Directory: /var/log/
Files to look at:
* messages
* syslog
* auth.log
* any firewall or iptables logs

To view more log files, you'll need root/sudo access.  Using **tail -f** is the easiest way to watch log files as they are being added to.

10.10 is way out of support (no patches) isn't it? You really should be on 10.04 (Apr 2015) or 12.04 (Apr 2017). Stay with LTS releases to have patches for longer periods.

---

