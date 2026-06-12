---
title: "Samba 3.5.11 + AD + OS X"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by sysc on 2012-03-06
Alright so we're migrating from OS X Server 10.x to Ubuntu for our file servers. We've tested performance and it's leaps an bounds better for network based home directories. The only issue we have run into so far is that 10.5.8 cannot seem to mount network based home directories. We're getting Error 80. 


SMB_OpenSession: - error = 80!


Every other OS is working fine, 10.6.x 10.7.x, Windows XP, Windows 7.


I am wondering what I am missing...

Here is my config


[global]

workgroup = xxxxx
realm = xxxx.xxx.xxx
server string = %h server (Samba %v, Ubuntu)
netbios name = xxxxx
wins server = xxxxxxx
password server = xxx.xxxx.xxx
enable privileges =Yes
allow trusted domains = No
ntlm auth = yes
dos charset = CP437
dns proxy = no
name resolve order = host wins bcast
log file = /var/log/samba/log.%m
max log size = 1000
log level = 3
security = ADS
encrypt passwords = yes
socket options = TCP_NODELAY
time server = Yes
idmap uid = 16777217-33554431
idmap gid = 16777217-33554431
winbind enum users = yes
winbind enum groups = yes
printcap name = cups
printing = cups
cups options = raw
template shell = /bin/bash
read raw = no
level2 oplocks = true


#======================= Share Definitions =======================
[homedir]
comment = Share Data
path = /data/homedir
read only = No
create mask = 0775
directory mask = 0775
browsable = Yes
public = Yes

---

