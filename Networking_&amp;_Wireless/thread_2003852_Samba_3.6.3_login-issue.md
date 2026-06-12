---
title: "Samba 3.6.3 login-issue"
date: 2012-06-14
forum: Networking &amp; Wireless
---

### Post by mythjunkie on 2012-06-14
Hi,

I had older version of Mythbunty with Samba Version 3.5.8.

I connect to it using PC (Win2k, WixXP, Win7).
I also connect to it from my Brite-View BV-5005HD.
Everything worked like a charm.

Now I upgraded to Mythbuntu 12.4 which comes with 3.6.3.

I can still connect all my PC's.
But for some reason Brite-View BV-5005HD give me a login error.

Config file was copied over so they are exactly the same on both version.

=================== Config global options ===================
[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
follow symlinks = yes
wide links = yes
unix extensions = no
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share
map to guest = bad user
load printers = no
show add printer wizard = no
printing = none
printcap name = /dev/null
disable spoolss = yes
usershare allow guests = yes
guest account = nobody
client lanman auth = yes
lanman auth = yes
================== End Config header options ================

I tried to compile Samba 3.5.8 so I can replace 3.6.3.
But that is another battle - compiling it is harder than I thought.
At least for my skill level.

Please help.

I checked the logs under /var/log/samba.
They were clean. No errors reported.

Please help cannot accees any of my media now.

---

### Post by mythjunkie on 2012-06-15
this is solved ..

there were several things that I did .. one of them fixe it ..

I follows the advice from the following threads :

[http://ubuntuforums.org/showthread.php?t=2003344&highlight=samba+login](http://ubuntuforums.org/showthread.php?t=2003344&highlight=samba+login)

[http://ubuntuforums.org/showthread.php?t=1958165&highlight=samba+login](http://ubuntuforums.org/showthread.php?t=1958165&highlight=samba+login)

re-started Samba ...

and then on my CinemaTube .. I did not put in the Password, only the user id .. that seems to work ...

---

