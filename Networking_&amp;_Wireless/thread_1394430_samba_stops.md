---
title: "samba stops"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by Tourdog on 2010-01-30
Samba shows on my System - Admin - samba menu.  But, I cannot get the "create samba share" menu to record anything.  It has 1 line of data showing "printers- printer" but using "help" along side nothing seems to install although you can type/print whatever but "ok" means it just sits there. 
 I am trying to link up to a XP laptop "homegroup" for file sharing.  Both computers are on my wifi.

The following plugins were installed via Synaptics:

smb client             2:3.4.0-3ubuntu5.4
python-smbc         1.0.6-0ubuntu2
libpam-smbpass    2.3.4.0-3ubuntu5.4
libwbclienst0               "
samba-common-bin     "
sambadoc                   "  
samba                        "
samba common           "
system-config-smba  1.2.63-ubuntu4

Initially clicking on "samba" brings this up:
"warning: some lines couldn't be understood while reading the configuration file  /etc/samba/smb.conf.  these may be unknown configuration directives samba plugins but could also be configuration errors."   You continue on and the results are a static "samba server menu" accepting what you type but doing nothing with it upon OK.

Do I need to delete 1 or > of the downloads from synaptics or am I missing 1?
What is my next step?  

TIA  :) !     This "samba" is a devil to get working!

---

### Post by Tourdog on 2010-01-30
I tried this :   

tourdog@PJK3:~$ dpkg -l | grep samba

ii  samba                                 2:3.4.0-3ubuntu5.4                                      SMB/CIFS file, print, and login server for U

ii  samba-common                          2:3.4.0-3ubuntu5.4                                      common files used by both the Samba server a

ii  samba-common-bin                      2:3.4.0-3ubuntu5.3                                      common files used by both the Samba server a

ii  samba-doc                             2:3.4.0-3ubuntu5.4                                      Samba documentation

ii  system-config-samba                   1.2.63-0ubuntu4                                         GUI for managing samba shares and users

tourdog@PJK3:~$ 

Doesn't seem the extra files should be a problem.  Or?

---

