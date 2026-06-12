---
title: "Samba and Office 2003"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by megarainman on 2009-06-10
I run a samba fileserver in an enterprise environment.  Everything seems to work pretty well except one thing. 

When a try to open a Word or an Excel document... it can takes about 20 seconds before it opens.  The same thing happens when I try to close the document.  

Normally it has nothing to do with the network because all the rest of file-types like pdf's, avi's go very fast...  

Search on the internet long time but couldn't find any solution.

Who can help me?  Below you can find my smb.conf file.

```

[global]

workgroup = MOT
realm = MOT.LOCAL
load printers = no
preferred master = no
local master = no
server string = fileserver
password server = 192.168.2.200
encrypt passwords = yes
security = ADS
netbios name = fileserver
client signing = Yes
dns proxy = No
wins server = 192.168.2.200
idmap uid= 10000-20000
idmap gid= 10000-20000
winbind separator = +
winbind enum users = Yes
winbind enum groups = Yes
winbind use default domain = Yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
log file=/var/log/samba/sambakristof.log
max log size = 50

[Data]
comment = Data
path = /home/data
read only = no
guest ok = no
oplocks = yes
map archive = no
browseable = yes
map acl inherit = yes
inherit permissions = yes
nt acl support = no


```Thanx in advance,
Kristof

---

