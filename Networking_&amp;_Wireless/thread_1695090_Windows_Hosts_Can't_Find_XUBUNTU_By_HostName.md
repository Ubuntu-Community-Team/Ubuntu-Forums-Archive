---
title: "Windows Hosts Can't Find XUBUNTU By HostName"
date: 2011-02-25
forum: Networking &amp; Wireless
---

### Post by MarquisEXB on 2011-02-25
Have to say that as a long time Windows user, I'm loving Xubuntu!

Anyway I have Xubuntu 10.04 that I use for file share on my home network. I have samba setup, and I can access the shares from my Windows XP PCs by ip address. However I don't seem to be able to reach it by hostname. In attempting to troubleshoot this I've installed winbind, but that didn't seem to help. I'm stumped. Below are my config files. Any help would be greatly appreciated.

```

[global]
panic action = /usr/share/samba/panic-action %d
workgroup = "Workgroup"
netbios name = "fISHBONE"
# added 2/18/2011
name resolve order = hosts wins bcast
invalid users = root
security = user
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
passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %
n\n .
obey pam restrictions = yes
pam password change = no
null passwords = no
hide dot files = no
#Share Definitions

[homes]
comment = Home Directories
browseable = yes
writable = yes
security mask = 0700
create mask = 0700

[ShareA]
path =  /Drives/ShareA
#read only = No
writeable = yes
# create mask = 0777
# directory mask = 0777
inherit permissions = yes
guest ok = no

```
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat wins
group:          compat wins
shadow:         compat wins

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

---

