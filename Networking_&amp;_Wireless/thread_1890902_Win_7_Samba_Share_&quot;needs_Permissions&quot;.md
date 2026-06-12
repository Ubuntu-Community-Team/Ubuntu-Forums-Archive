---
title: "Win 7 Samba Share &quot;needs Permissions&quot;"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by LANrover on 2011-12-04
Hey everybody,

I have a pretty decent computer setup, that I'm trying to get running.  I currently run ubuntu server 11.10 on a server-type box I've built that has 4x2tb caviar black drives in a raid 5 array.  I FINALLY got that set up this morning, and I'm trying to set up a samba share so that I can use this server for what it's truly intended for: Holding my media so I can access it from my workstation (win 7), laptop (backtrack5) over a VPN, and my Apple TV Set top box I've jailbroken and I'm running XBMC on.

Basically, I need to be able to get access into this server.  I also want to make it so that my little brother can put his movies on it (from his computer on the network) but into a different file so he doesn't delete anything important.

I have my RAID 5 array set up in /srv, and have created 3 directories inside:

/srv/www   <-- Used to include a symbolic link to my apache web server,
/srv/files    <--- Where I hold all my media/college materials/etc.
/srv/new    <--- Where I want my little brother to put everything so I can manually move it at a later time.

Basically, my Windows 7 computer (named Adam) can see everything on the shares on the server (named Lillith), but cannot write.  If there's only one computer that I can set up to write to this server, it's this one.

```
testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[Media]"
Processing section "[New]"
Processing section "[Web Server]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
  workgroup = SHARE
  server string = %h server (Samba, Ubuntu)
  security = SHARE
  map to guest = Bad User
  obey pan restrictions = Yes
  pam password change = Yes
  passwd program = /usr/bin/passwd %u
  passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\spassword:* %n\n *password\supdated\ssuccessfully* .
unix password sync = Yes
  syslog = 0
  log file = /var/log/samba/log.%m
  max log size = 1000
  name resolve order = lmhosts host wins bcast
  os level = 33
  dns proxy = No
  usershare allow guests = Yes
  usershare owner only = No
  panic action = /usr/share/samba/panic-action %d

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[Media]
  comment = File Server Share
  path = /srv/files
  browsable = yes
  guest ok = no
  read list = @home
  write list = @admin

[New]
  comment = User Added Data
  path = /srv/new/
  browsable = yes
  guest ok = yes
  read only = no
  create mask = 0755

[Web Server]
  comment = Web Site Data
  path = /srv/www
  browsable = yes
  force user = adam
  guest ok = yes
  create mask = 0777
```But whenever I try to write anything, I get an error message that says "You need permission to perform this action."

The folder itself has been chmod to 777, owned by the win7 computer's login, I've even tried to map the drive to Z:/ requiring credentials, but I'm completely lost here.  I've tried everything I can think of to get my Win7 Machine to have write permissions on this thing.

Any Insight would be greatly appreciated.

Edit:  I've only been working on the /www folder to get it to work, instead of changing every folder ever time....

Thanks,
Chuck

---

### Post by LANrover on 2011-12-04
Basically, I can't write to my samba shared linux server directory from my windows computer, even though the folders permissions are set to 777, the share's permissions are set to 777, and the mask is set to 777.

---

### Post by Stason on 2012-04-01
I have the same issue. Any solutions?

Could that be that the shared folder is ext4 and win7 simply cannot write to it?

---

### Post by gordintoronto on 2012-04-02
No.

You don't need to use Ubuntu Server for this, Ubuntu Desktop is a much better choice.

---

