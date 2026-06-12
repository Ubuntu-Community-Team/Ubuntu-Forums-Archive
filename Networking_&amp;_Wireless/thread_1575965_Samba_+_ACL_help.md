---
title: "Samba + ACL help"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by jps1x2 on 2010-09-16
Hi all,

i am new to this forum, i have problems with Samba (integrated to my Windows DOMAIN) and ACL. My Ubuntu Srv 10.04 is joining my DOMAIN correctly.

My /etc/samba/smb.conf with the only share created:

```
[global]
unix charset = LOCALE
realm=DOMNAVARTI
workgroup=DOMNAVARTI
security=ADS
password server=*
winbind separator=+
log level = 1
syslog = 0
log file = /var/log/samba/%m
max log size = 50
winbind uid=10000-20000
winbind gid=10000-20000
winbind enum users=yes
winbind enum groups=yes
template homedir=/tmp
template shell=/bin/false
interfaces = lo, eth0
bind interfaces only = true

[share]
path = /mnt/disco2/share
writable = yes
browsable = yes
```Using ACL, i have established following ACL permissions and default ACL permissions to following folder:

/mnt/disco2/share/CopiaSeguridad/JorgeP

```
#getfacl JorgeP

# file: JorgeP
# owner: DOMNAVARTI+jorgep
# group: root
user::rwx
group::---
other::---
default:user::rwx
default:user:DOMNAVARTI+jorgep:rwx
default:group::---
default:mask::rwx
default:other::---
```I would like that for new files and folders that user (the owner) has rwx, but group and other has --- (no permission to read, write or execute/search).

When using Samba i create a new file in JorgeP folder from a windows and permissions of file are like this:

```
# getfacl test.txt
# file: test.txt
# owner: DOMNAVARTI+jorgep
# group: DOMNAVARTI+usuarios\040del\040dominio
user::rwx
user:DOMNAVARTI+jorgep:rwx
group::r--
mask::rwx
other::---
```group is created r--, but default ACL in folder JorgeP group is ---

and when i create a folder in JorgeP folder from windows, permissions of folder are like this:

```
# getfacl test
# file: test
# owner: DOMNAVARTI+jorgep
# group: DOMNAVARTI+usuarios\040del\040dominio
user::rwx
user:DOMNAVARTI+jorgep:rwx
group::r-x
mask::rwx
other::r-x
default:user::rwx
default:user:DOMNAVARTI+jorgep:rwx
default:group::---
default:mask::rwx
default:other::---
```group is created r-x and other is created r-x , default ACL are --- both in JorgeP folder ACL.

How could i set default ACL configuration or Samba configuration to obtain permissions on new files and folders correctly?

Thank you very much in advance

Jorge

---

### Post by jps1x2 on 2010-09-17
Hi all,
 
yesterday i solved the problem chating on #samba IRC channel.
 
Modified file /etc/samba/smb.conf and the new share is like this:
 
```
 
[CopiaSeguridad]
create mask = 700
force create mode = 700
security mask = 700
directory mask = 700
force directory mode = 700
directory security mask = 700
path = /mnt/disco2/share/CopiaSeguridad
writable = yes
browsable = yes

```
 
 
Using that mask options new files and folders in that share are created with permissions rwx------ , that is what i need.
 
Thank you very much
 
Jorge

---

