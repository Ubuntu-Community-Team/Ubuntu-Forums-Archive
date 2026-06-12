---
title: "[SOLVED] SAMBA Share, from where?"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by n2stc on 2008-12-30
I have samba working thanks to many helpful posts.  I have a shared folder appearing, but don't see a reference to it any where in smb.conf.  Where else could it be coming from?

Thanks, 
Stan

---

### Post by eder.apt-get on 2008-12-30
Can you post the output of```
sudo cat /etc/smb.conf
```?

---

### Post by Iowan on 2008-12-30
Shares should be defined under either */var/lib/samba/usershares* or  */etc/samba/smb.conf*.

---

### Post by n2stc on 2008-12-30
> **eder.apt-get said:**
> Can you post the output of```
sudo cat /etc/smb.conf
```?

cat /etc/smb.conf  Does not exist.

The result of "cat /etc/samba/smb.conf"  is:

```


[global]
; General server settings
netbios name = sc1-2

workgroup = ms_home
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
null passwords = true
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

wins support = yes

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
[homes]
valid users = stan
create mask = 0600
browseable = no
read only = no
veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /home/stan/Documents
;admin users = stan
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
guest ok = yes
write list = root
create mask = 0664
directory mask = 0775

[HANDY_BACKUP]
path = /media/XP_SHARE/XP_UNIX_Share/handy_backup
guest ok = yes
read only = no
case sensitive = no
strict locking = no
;msdfs proxy = no

[testing]
path = /home/stan/Public/
guest ok = yes
read only = no
case sensitive = no
strict locking = no

```

The share I cannot account for is "stan"  It is seen from Windows XP and Dolphin, Konquerer etc.  I did create it once, but don't see a reference to it now.  I am running it on KDE & Gutsy 7.1

Thanks!
Stan

---

### Post by borahshadow on 2009-01-01
It is likely coming from the homes section. That creates a share for each user's home directory.

---

### Post by Iowan on 2009-01-01
Is it under */var/lib/samba/usershares*?

---

### Post by borahshadow on 2009-01-01
No in the config file that you posted there is a [homes] section that is the most likely place for it to come from. A quick google will tell you about homes, but basically it creates a share of each user's home directory.

---

