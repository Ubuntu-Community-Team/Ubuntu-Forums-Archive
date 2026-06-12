---
title: "samba sharing of a mounted remote volume"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by santini@rotoin.it on 2011-04-21
Hello everybody,
I'm new to this forum and quite new to Ubuntu Server.
I'm running 10.04 server on a Mac G5 with 2 network interfaces, one pointing to my network (192.168.0.x) and the other to a local partner network (192.9.100.x) with which we share a network volume to give/take PDF files.
My client environment is MAC OS X (from 10.4 to 10.6) and until now only one client (with 2 nics) was connected to that volume: we don't have layer3 switches to do static routes over the two networks, so I decided to use my Ubuntu Server Mac to do this (it's also my new syslog server...).

Nics are configured correctly, and the local share (192.168.0.x) is well seen by everybody. But, when I mount the remote volume (192.9.100.x) to THAT shared folder, nobody is able to connect to the samba share (that now lists the remote volume directory...). The MAC OS X tells "unable to unmount the volume". 

IP forwarding is also activated on /etc/sysctl.conf

Here is a part of my smb.conf file

#======================Share Definitions ====================
	
[TERA]
   comment = Tera Condiviso
   path = /TERA
   public = yes
   read only = no
   guest ok = no
   writable = yes
   create mask = 0777
   NT acl support = yes
   inherit permissions = yes
   inherit acls = yes
   map acl inherit = yes
   map archive = no
   map readonly = no
   store dos attributes = yes

Any idea?
I don't want to do static routes over the two nics, because any MAC OS X client needs to add software to manage this architecture (while Windows not... pity...)
Thanks

Dimitri

---

### Post by BbUiDgZ on 2011-04-21
rule out your smb.conf, bakup your old config

```
mv /etc/samba/smb.conf /etc/samba/smb.conf.backup
```

now create a new conf 

```
nano /etc/samba/smb.conf
```

and add

```

[global]
        lanman auth = Yes
        netbios name = machinename
        server string = See me NT
        default = global
        workgroup = your.workgroup
        os level = 20
        client lanman auth = Yes
        auto services = global
        security = share
        wins support = true

[sharename]
    comment = anything
    path = /path/to/your/share
    read only = no
    public = yes

```

edit the parts like the sharename, path and workgroup

restart samba
```
/etc/init.d/samba restart
```

check your share

---

### Post by NickRiviera on 2011-04-26
Hello,
it's always me with a different account (the first one had a login issue not yet fixed by administrators).
I've tried your suggestion, BbUiDgZ, but with no result: when a mount the remote volume on the shared folder nobody form a Mac can (no longer) connect to the share.

here is a part of my smb.conf file:

```

[INDENT][FONT="Courier New"][global]
   lanman auth = Yes
   netbios name = SrvRotoSyslog
   server string = See me NT
   default = global
   workgroup = WORKGROUP
   os level = 20
   client lanman auth = Yes
   auto services = global
   security = share
   wins support = true[/FONT][/INDENT]

```

(this is exactly what you asked me to do)


```
[INDENT][FONT="Courier New"][TERA]   
   comment = Disco Tera
   path = /TERA
   public = yes
   read only = no
   guest ok = no
   writable = yes
   create mask = 0777
   NT acl support = yes
   inherit permissions = yes
   inherit acls = yes
   map acl inherit = yes
   map archive = no
   map readonly = no
   store dos attributes = yes
[/FONT][/INDENT]
```

(this is a legacy of an old samb.conf file that worked well with ACLs, in both Mac and Win environments).

maybe something in the two definitions conflict?
thanks

---

