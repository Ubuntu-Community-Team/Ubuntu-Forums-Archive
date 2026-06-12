---
title: "samba setting"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by blackcloud on 2009-12-29
here my smb.conf can i know what wrong with this script, i opened share and not open. and i see in my log :
> 2009/12/27 17:51:26, 0] smbd/service.c:make_connection_snum(1012)
  '/home/share/doc' does not exist or permission denied when connecting to [Shar

and this is my script
> global]
log file = /var/log/samba/log. %m
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n $
obey pam restrictions = yes
map to guest = bad user
encrypt passwords = true
public = yes
passdb backend = tdbsam
passwd program = /usr/bin/passwd %u
wins support = yes
max wins ttl = 18748800
min wins ttl = 60
netbios name = mhku
server string = %h server (Samba, Ubuntu)
path = /var/tmp
preferred master = yes
domain master = yes
local master = yes
workgroup = WORKGROUP
syslog = 0
panic action = /usr/share/samba/panic-action %d
usershare allow guests = yes
max log size = 1000
pam password change = yes
name resolve order = wins bcast hosts lmhosts
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
os level = 65
announce as = WfW
guest ok = Yes
usershare allow guests = Yes
name cache timeout = 0
nt status support = yes
nt pipe support = yes
winbind cache time = 60
idmap uid = 50-9999999999
idmap gid = 50-9999999999
idmap cache time = 120
lm announce = yes
lm interval = 10
enhanced browsing = Yes
browse list = yes
[Share]
        comment = File Server Share
        path = /home/share/doc
        read only = No
        create mask = 0777
        directory mask = 0777


thank you before

---

