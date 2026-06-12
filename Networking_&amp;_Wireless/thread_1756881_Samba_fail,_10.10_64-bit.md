---
title: "Samba fail, 10.10 64-bit"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by Dzugavili on 2011-05-12
I'm using samba to share the contents of a few NTFS drives for use with my media player (ASUS O!Play R1, if that matters), connected over the network.

The folders themselves appear, but any attempt to log into the directories fails. Even if the directories support guest access. The only response I can get is "incorrect password" or something along those lines.

Previously, samba was working fine. I recently installed updates (I really should stop doing that, it never works out) and samba no longer functions.
Note: I have not changed my samba config since I got it working the first time about 4 months ago. Unless the update also makes that file useless, testparm shouldn't need to be run; I did anyway, because I know someone will ask and there might be a hack to that which will fix it.

testparm -sp
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    usershare owner only = No
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

Now, I read that samba4 is out in alpha (might be an old thread so it might be gold now) and that it doesn't seem to work as well as samba3.

1. How would I check my samba version? Samba4 seems to be the only one in the repository, I'm guessing I have samba4 now.
2. But if samba3 is still the active version, is it actually possible that someone was stupid enough to flag samba4 as an upgrade to samba3 when we know that it doesn't work with samba3 configs? How would I roll back? How would I adapt the file to work with samba4?
3. Is there another solution?

*Edit:*
The program 'samba' is currently not installed.  You can install it by typing:
~$ samba4
No command 'samba4' found, did you mean:
 Command 'samba' from package 'samba4' (universe)
~$ sudo apt-get install samba
samba is already the newest version.
~$ samba
The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4

And sudo apt-get install samba4 pulls down a new package.

I HAVE NO IDEA WHAT'S GOING ON HERE. I think a couple of those messages are contradictory.
Maybe it'll work now. Rebooting...

*Edit:*
Pre-reboot:
 * Starting Samba 4 daemon samba  
Unknown parameter encountered: "usershare owner only"
Ignoring unknown parameter "usershare owner only"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"

Edit:
Seems to work now.
Didn't work on first reboot or second, but the third time was the charm.

Not exactly sure what the problem was.

---

