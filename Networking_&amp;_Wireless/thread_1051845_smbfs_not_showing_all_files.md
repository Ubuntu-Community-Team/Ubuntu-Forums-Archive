---
title: "smbfs not showing all files"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by specialcharacter on 2009-01-27
I'm having a strange problem with samba and smbfs accessing a windows XP share.

Using smbmount, I can access the share fine, but only a few of the directories show. The directory in question is my music collection, so contains around 500 directories, which in turn contain around 10,000 files. Out of these, only around 40 directories are shown in gnome.

When I try to view the folder using samba in gnome, I get the following error: "Sorry, could not display all the contents of "music on adams": Invalid argument".

There seems to be very little on google about the above error, but I am wondering if it is to do with special characters in the windows share?

My smb.conf looks like:

```
[global]
netbios name = ADAMS-LAPTOP
server string = ADAMS-LAPTOP
workgroup = MSHOME

announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

name resolve order = bcast lmhosts wins host
wins support = yes

syslog = 1
syslog only = yes

[home]
path = /home/adam
available = yes
browsable = yes
writable = yes
guest ok = yes
public = yes


```

---

### Post by specialcharacter on 2009-01-30
bump?

---

