---
title: "i keep having to restart samba"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by roop_s on 2010-10-25
a few times a day I have to run sudo service smbd restart on my primary server to get samba working again. by working i mean being able to see the server in the workgroup and being able to type smb://phoenix/ and have a result. please help me troubleshoot this.

env: server: 10.10 x64, clients: 10.10 32 & 64, 10.04, winxp all affected the same way

last time it occurred within 2 hours after a reboot. here's the config. I've been commenting out lines that I wasn't sure of in an attempt to troubleshoot this.

```

  1 [global]
  2 ; General server settings
  3 netbios name = phoenix
  4 server string = ""
  5 workgroup = WORKGROUP
  6 announce version = 5.0
  7 socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
  8 
  9 passdb backend = tdbsam
 10 security = user
 11 null passwords = false
 12 username map = /etc/samba/smbusers
 13 name resolve order = wins hosts bcast
 14 
 15 #os level = 99
 16 wins support = yes
 17 #local master = yes
 18 #preferred master = yes
 19 #domain master = yes
 20 #interfaces = eth0
 21 #bind interfaces only = true
 22 
 23 syslog = 1
 24 syslog only = yes
 25 
 26 [Home]
 27 path = /home/roop
 28 browseable = yes
 29 read only = no
 30 guest ok = no
 31 create mask = 0644
 32 directory mask = 0755
 33 force user = roop
 34 
 35 [Audio]
 36 path = /home/roop/Audio
 37 browseable = yes
 38 read only = no
 39 guest ok = no
 40 create mask = 0644
 41 directory mask = 0755
 42 force user = roop
 43 
 44 [Documents]
 45 path = /home/roop/Documents
 46 browseable = yes
 47 read only = no
 48 guest ok = no
 49 create mask = 0644
 50 directory mask = 0755
 51 force user = roop
 52 (a few more shares)

```

---

### Post by roop_s on 2010-10-27
i'm now having this issue on two PCs.

Another computer that usually isn't rebooted for months started having the problem today. One thing on the reboot was a kernel upgrade 2.6.32-22-generic SMP. The symptoms were the same, SAMBA shares were not accessible after a reboot. Restarting the SAMBA service got it working again. After a little bit over an hour it stopped working and a service restart brought it back. No crashes reported, no cores etc.

I rebooted back to 2.6.32-21-generic SMP. Problem is no longer occurring - after several hours I haven't had to restart smbd. I'm running 2.6.32-25-generic SMP on the other problematic system. I've rolled it back to 2.6.32-21-generic SMP as well. On bootup samba was ok, I'll see how it works after a few hours.


Computer #1 (what the first post is based on):
Ubuntu 10.10 kernel 2.6.32-25 is problematic, 2.6.32-21 is being tested
smbd/nmbd version 3.5.4

Computer #2:
Ubuntu 10.04 kernel 2.6.32-22 is problematic, 2.6.32-21 works
smbd/nmbd version 3.4.7

---

### Post by roop_s on 2010-10-28
After 12 hours I have not had to restart samba on either of the affected systems. the 2.6.32-21 kernel is working well. I learned a valuable lesson from this: just like any new version of software, unless there is a specific fix that you need from the new code, don't upgrade. It could be painless or you could be troubleshooting it for weeks. For the faint of heart who do not want to replace kernels, I hope ubuntu becomes more polished in future releases. Re-install isn't always an option and now that only 10.04.1 is available for download which doesn't come with 2.6.32-21, a simple re-install is not the answer.

How to replace your kernel with an older one:
[http://ubuntuforums.org/showthread.php?t=1601964](http://ubuntuforums.org/showthread.php?t=1601964)

Here are three pages of complaints from people who had a good experience with 2.6.32-21 and were royally hosed with 2.6.32-22:
[http://ubuntuforums.org/showthread.php?t=1473719](http://ubuntuforums.org/showthread.php?t=1473719)

---

