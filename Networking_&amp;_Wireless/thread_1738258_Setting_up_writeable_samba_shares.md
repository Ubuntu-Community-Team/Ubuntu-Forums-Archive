---
title: "Setting up writeable samba shares"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by Ptallqvist on 2011-04-24
What I'm trying to do:
Set up my samba server so that other computers can log in with username and password and read/write some folders.

What I've got so far:
I can access and automount guest shares. When I try to access the read-write shares via ubuntu gui (Places-connect to server), I get stuck at the login. ("password required for share user1home on 192.168.11.64") 
I try to enter the username (user1), domain (group1) and password, but I get nowhere. After I click cancel I get the error "Could not display "smb://192.168.11.64/user1home, The file is of an unknown type".

Here's my smb.conf:
```
[global]
   workgroup = group1
   hosts allow = 192.168.11.0/25
   hosts deny = all
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   name resolve order = lmhosts host wins bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

[music]
path = /home/user1/public/music
guest ok = yes
browseable = yes
read only = yes

[pics]
path = /home/user1/public/pics
guest ok = yes
browseable = yes
read only = yes

[user1home]
path = /home/user1
comment = user 1 home read/write
browseable = yes
valid users = user1
writable = yes
guest ok = no
```

So, what am I doing wrong? Thank you in advance.

---

### Post by Morbius1 on 2011-04-24
Did you create a samba password for user1 on the server?

```
sudo smbpasswd -a user1
```

---

### Post by Ptallqvist on 2011-04-24
No, I did not :oops:

I synced the passwords with webmin, but apparently I understood that a bit wrong. Now that I gave user1 the samba password, everything's working as it should.

Thanks a lot!

---

