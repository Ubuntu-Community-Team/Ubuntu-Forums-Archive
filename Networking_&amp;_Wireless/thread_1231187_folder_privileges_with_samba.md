---
title: "folder privileges with samba"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by Surendil on 2009-08-04
Hello everyone.
I been working up with samba shared folders, but have some troubles with users/folder privileges.
Users: ale jvillar

I got a folder named "BACKUP"
users ale and jvillar can read/write this folder
inside "BACKUP" is another folder named "MAIL BACKUP"
i want user ale to read/write this folder and user jvillar only read.
Even though i tried everything i could think of nothing worked out the way i wanted too.
Did anyone solved this?

Here is my smb.conf



[global]
workgroup = shibusen
netbios name = FileServer
server string = FILE SERVER
os level = 64
preferred master = no
domain master = no
local master = no
wins support = yes
debug level = 2
log file = /usr/local/samba/var/log.%U
max log size = 50
security = user
encrypt passwords = yes
logon script = logon.bat
logon path = \\%L\profiles\%U
logon drive = H:
logon home = \\%L\%U
time server = yes
add machine script = /usr/sbin/useradd -s /bin/false -d /dev/null '%u'

[backup]
path = /home/backup
comment = backup
valid users = jvillar ale
write list = jvillar ale
read only = no
available = yes
browseable = no
writable = no
guest ok = no
public = no

[mail backup]
path = /home/backup/mails
comment = mail backup
valid users = ale jvillar
write list = ale
read only = no
available = yes
browsable = yes
writable = no
guest ok = no
public = no

---

