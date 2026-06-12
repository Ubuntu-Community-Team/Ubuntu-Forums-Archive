---
title: "autofs mounts shares only after autofs restart (Ubuntu 12.04)"
date: 2012-08-06
forum: Networking &amp; Wireless
---

### Post by uusrs on 2012-08-06
Hello,

I mount Samba shares using autofs. It works, but only autofs restart.

When I start Linux, I see autofs running:
[B]uusrs@solace:~$ sudo service autofs status
[sudo] password for uusrs: 
autofs start/running, process 1654
uusrs@solace:~$ [/B]

However, no shares mounted. No errors in syslog.

After that, I restart autofs:
[B]uusrs@solace:~$ sudo service autofs restart
autofs stop/waiting
autofs start/running, process 3867
uusrs@solace:~$[/B]

After restart all shares appear and I can work with them. However, I don't want to restart autofs manually for mounts to work! I'm trying to make autofs work just after the system's start without any manual commands.

Does anybody know how to do this?

Thank you!

P.S. I had another issue before with autofs  ([http://ubuntuforums.org/showthread.php?t=1999791](http://ubuntuforums.org/showthread.php?t=1999791))  but solved it,  thanks to the community!

---

### Post by Toz on 2012-08-10
Quick question: Based on your auto.master file from the previous thread, is your home directory/partition encrypted? If so, autofs won't have access to it during the boot cycle.

---

### Post by uusrs on 2012-08-11
Hello Toz, many thanks for your help! My home dir is encrypted indeed.

To implement a workaround, I created /mnt/network directory, pointed a symlink to it from my home dir, and edited the path in my auto.master file. Here it is my auto.master:
/mnt/network  /etc/auto.uusrs --timeout=60 --ghost

It works now and the network shares are available after restart.

Appreciate your help!

---

