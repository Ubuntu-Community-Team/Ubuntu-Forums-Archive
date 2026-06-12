---
title: "Gmailfs: how to use it?"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by xaber1488 on 2009-07-05
Hi there!
I installed gmailfs by apt-get install gmailfs, but when i mount the fs by mount.gmailfs none /home/xaber/gmfs -o username=gmailuser@gmail.com,fsname=zOlRRa -p, it is mounted correctly,but I can't use it! For example, if, in my home dir, I type "ls", it says to me that the device gmfs is full... The same if I open gmfs and try to create a dir: it says that the device is full (obviously, my gmail box is not full)! Instead, if I try to open it with nautilus, I get the message that no application is installed to manage that object!
How can I use gmailfs?

Thanks in advance!

---

### Post by xaber1488 on 2009-07-06
A little up!

---

### Post by verylazyguy on 2009-07-18
I am having the same issue.  The mount command has an exit code of 1 but I don't know what that means.

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
python                7.2G  181M  7.0G   3% /mnt/gmailfs

$ touch /mnt/gmailfs/test
touch: cannot touch `/mnt/gmailfs/test': No space left on device

---

### Post by mhennig1 on 2009-07-21
Hi all,

same problem ("No space left on device") on Fedora 10 with python-libgmail-0.1.11 and fuse-gmailfs-0.8


Any solution here on Ubuntu?

gmailfs dies immediately after starting it (log level is DEBUG):

07/20/09 18:44:29 ERROR      OpenSSLProxy is missing. Can't use HTTPS proxy!
07/20/09 18:44:29 INFO       waiting for /root/gmail to become a mountpoint
07/20/09 18:44:29 INFO       Starting gmailfs in child process (PID 5314)
07/20/09 18:44:29 INFO       Mountpoint: /root/gmail
07/20/09 18:44:29 INFO       Named mount options: {'password': '********'}
07/20/09 18:44:29 WARNING    mount: warning, should mount with username=gmailuser option, using default
07/20/09 18:44:29 WARNING    mount: warning, should mount with password=gmailpass option, using default
07/20/09 18:44:29 WARNING    mount: warning, should mount with fsname=name option, using default
07/20/09 18:44:31 INFO       Connected to gmail
07/20/09 18:44:32 DEBUG      get stat:/
07/20/09 18:44:32 DEBUG      check getnodemsg:/
07/20/09 18:44:32 DEBUG      ind:0
07/20/09 18:44:32 DEBUG      dirpath:/ name:
07/20/09 18:44:32 DEBUG      ind:0
07/20/09 18:44:32 DEBUG      dirpath:/ name:
07/20/09 18:44:32 INFO       Sent message failed
07/20/09 18:44:33 INFO       Sent message failed
07/20/09 18:44:33 INFO       Sent message failed
07/20/09 18:44:33 ERROR      Send failed too many times
07/20/09 18:44:33 ERROR      gmailfs child died, exiting...

---

