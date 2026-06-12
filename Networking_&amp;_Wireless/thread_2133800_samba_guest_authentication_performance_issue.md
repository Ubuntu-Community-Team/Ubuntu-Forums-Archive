---
title: "samba guest authentication performance issue"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by freesbee on 2013-04-09
I am experiencing a very strange issue with Samba 3.6.3 on Ubuntu 12.04.2 Server regarding guest authentication. Whatever I did the situation is very strange, and I cannot figure out a reasonable explanation. I have quite much experience in hardware and Win environment, but I've been playing with Ubuntu since about 1 year, so I'm quite new here.

I have been searching extensively for a problem similar to mine... nothing found. Maybe the solution is very easy and I just didn't find it. I would be very grateful if anybody could point me to the right direction.

**Scenario**
I have 2 twin machines:

[FONT=lucida sans unicode]Linux **** 3.5.0-27-generic #46~precise1-Ubuntu SMP Tue Mar 26 19:33:56 UTC 2013 i686 i686 i386 GNU/Linux[/FONT]

running on both of them Ubuntu Server 12.04.2 + Samba 3.6.3
On one of the two machines (the one experiencing the problem), also

[FONT=lucida sans unicode]Apache/2.2.22 (Ubuntu) PHP/5.3.10-1ubuntu3.6 with Suhosin-Patch[/FONT]

is running, working perfectly fine.

On both machines samba is used to share certain public RO and RW folders (by "public" I mean that everybody should be able to read/write any kind of file). All password protected folders work perfectly.

**Problem** ](*,)
On such public shares, I am experiencing only on ONE of the two machines about 2 seconds delay when a **guest user** enters the folder. This happens only the first time, and only for guest users (in my specific case mapped to **nobody**): after entering the folder once, the next time the access is immediate (till next restart of smbd). I desperately tried any kind of suggestion that I have found (included [FONT=courier new]map to guest = bad user / bad password[/FONT]), but the result is still the same.

[FONT=courier new]smb.conf[/FONT] files are THE SAME on both machines, [FONT=courier new]nobody:nogroup[/FONT] are the same, and even permissions on folders are the same.
For my specific use of those shares (they are RO software repositories and RW log files locations for about 50 windows clients), I need them to react immediately, as soon as the call is done. If each time one client calls one of them it has to wait 2 seconds, the performance of the entire system will be much lower.

I tried to read if something is going wrong in
[FONT=courier new]/var/log/samba/log.*[/FONT]
files, but I only find one empty file per each client accessing the shares as guest.

Of course a possible solution would be to move them to the machine working fine... but I would like to keep that machine for other experiments.

Again: the problem is coming only on [my_upd] and [pub], while the [pwdShare] works perfectly on both machines.

Here following my smb.conf. If anybody can help would be much appreciated...

[FONT=courier new][global]
 workgroup = <myDomain>
 server string = %h smb fileserver
 security = user
 encrypt passwords = true
 map to guest = Bad User
 guest account = nobody
 obey pam restrictions = Yes
 pam password change = Yes
 passwd program = /usr/bin/passwd %u
 passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
 unix password sync = Yes
 syslog = 0
 log file = /var/log/samba/%m.log
 max log size = 1000
 dns proxy = No
 usershare allow guests = Yes
 panic action = /usr/share/samba/panic-action %d
 idmap config * : backend = tdb

[my_upd]
 path = /myPath/my_upd
 browsable = no
 guest ok = yes
 read only = yes
 comment = software update repositories

[pub]
 path = /myPath/share
 browsable = yes
 guest ok = yes
 read only = no
 create mask = 0660
 directory mask = 0770
 force user = nobody
 force group = smbusers
 comment = %h public folder

[pwdShare]
 path = /myPath/pwdShare
 browsable = yes
 guest ok = no
 read only = no
 write list = @myGroup
 create mask = 0660
 directory mask = 0770
 force group = smbusers
 comment = pwd shared folder [/FONT]

---

