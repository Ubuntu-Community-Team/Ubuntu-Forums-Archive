---
title: "Samba troubles (ubuntu 10.04)"
date: 2010-08-08
forum: Networking &amp; Wireless
---

### Post by tohvanah on 2010-08-08
A few funny issues. Been running all over the forums, google, etc. changing smb.conf, removing, installing samba....ech.

**Guest and User Access**
[INDENT]_When smb.conf is set to "security = user" _
[INDENT]when I login as user "super", I can successfully access all shares (this is desired behavior)
I am **unable** to login as a guest
[/INDENT]

_When smb.conf is set to "security = share"_
[INDENT]when I login as user "super", I can **only** access the public share. Both shares still appear.
when I login as a guest I can access the public share; access is denied for the private share (this is desired behavior)
[/INDENT]
[/INDENT]

**Shared Folders**
[INDENT]_"Sharing services are not installed"_
[INDENT]No matter how I install Samba (whether thought Synaptic, Ubuntu Software Center or following *this* dialogue box) this message appears...over and over. 

Not a big issue for me, but annoying and poor show for Ubuntu...
[/INDENT]
[/INDENT]

Here's my smb.conf:
```
[global]
workgroup = workgroup
   server string = %h server (Samba, Ubuntu)
   log file = /var/log/samba/log.%m
  max log size = 1000
   syslog = 0
   map to guest = bad user
guest account = nobody
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
security = user

[private]
	path = /home/super/Downloads
	browseable = yes
	available = yes
	writeable = yes
	valid users = super

[public]
	path = /home/super/Public/
	browseable = yes
	available = yes
	writeable = yes
	guest ok = yes
```

my /etc/samba/smbusers:
```
root = administrator
nobody = guest pcguest smbguest

```

thanks!

---

### Post by tohvanah on 2010-08-11
bump

---

### Post by tohvanah on 2010-08-19
bumpity

... :)

---

