---
title: "amba giving me so much grief (can't connect to samba share from windoze)"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by benkenobi1601 on 2010-01-31
Hi all, I have spent days and days trying to fix allegedly such a simple kind of issue, but I have just lost too many hairs and at this point I am giving up on getting a nice simple linux server if you all can't figure it either. 
 
Anyways, I have a linux server running jaunty jackalope, I've got the newest samba version installed (I've installed and uninstalled nearly 10 times), here is my smb.conf file:
 
[global]
panic action = /usr/share/samba/panic-action %d
workgroup = workgroup
netbios name = "Server"
invalid users = root
security = user
username map = /etc/samba/smbusers
wins support = no
log file = /var/log/samba.log
log level = 3 
max log size = 1000
syslog = 1
encrypt passwords = true
passdb backend = smbpasswd
socket options = TCP_NODELAY
dns proxy = no
passwd program = /usr/bin/passwd %u
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no
 
#Share Definitions
 
[homes]
        comment = Home Directories
        browseable = yes
        writable = yes
        security mask = 0700
        create mask = 0700
 
[ben]
path = /home/ben
available = yes
browsable = yes
public = yes
writable = yes
 
[test]
path = /home/ben/test
available = yes
valid users = ben
read only = no
browsable = yes
public = yes
writable = yes
 
[home]
path = /home
available = yes
browsable = yes
public = yes
writable = no
 
I do realize it is pretty big and messy but this is a result of all the little parameters I've found on the interest that would have supposedly fixed my issue. The main issue is that I can't connect to any of the 3 samba shares that you can see above from any of [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]my [/FONT][/FONT][/COLOR][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]computers[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") ( i have one xp and one vista, neither can connect.)  
 
I try to connect by doing 192.168.1.106/home/ben (I found the IP by doing ifconfig, wher e i got inet addr:192.168.1.106). The strangest thing is that the first day I installed samba, the thing worked fine, I could transfer files onto the share between the server and the computers. The next day, it didn't work, and the weirdest thing was that when I tried to figure out what was wrong, I did ifconfig and the ip had changed to 192.168.1.106 from 192.168.1.102. I don't know what caused the change, but I found it very weird. The other day it changed to 192.168.1.105 as well, but now it's back to .106. This probably has something to do with it. IDK, I am a very big [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]linux[/FONT][/FONT][/COLOR][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") noob which is something you can probably tell by now.
 
 
So the error I get when I do a 192.168.1.106/home/ben from one of my computers is the standard "connection interrupted" in firefox or the "internet explorer cannot display the webpage" in IE. SO FRUSTRATING!!!
 
Before you ask, yes, I have made a username for samba as ben and made a password for it.  
 
Any help would be so greatly appreciated, this project is the first time I have tried linux and I feel like an idiot

---

### Post by mongr31 on 2010-01-31
Configuring Samba has always been a nightmare for me. I've been using webmin lately to do all my samba config for me. It works pretty good.

---

