---
title: "How to give everyone access to my samba share?"
date: 2005-12-15
forum: Networking &amp; Wireless
---

### Post by pcatiprodotnet on 2005-12-15
I want to set up a public samba share folder.  How do I give everyone Read access to it?  It keeps asking them for a password.  Thanks, -pc

{solved}

sudo gedit /etc/samba/smb.conf

[global]
guest ok = yes
restrict anonymous = no
protocol = LANMAN2
security = user
username map = /etc/samba/smbusers
encrypt passwords = yes
passdb backend = smbpasswd
guest account = nobody
invalid users = root
socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192
domain master = yes
max protocol = NT
ldap ssl = No
server signing = Auto
os level = 21
map to guest = Bad User

[share]
path = /home/MyUserId/share
available = yes
browseable = yes
public = yes
writable = no

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable = yes
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes

[cdrom]
   comment = Samba server's CD-ROM
   writable = no
   locking = no
   path = /cdrom
   public = yes

---

### Post by davidsrsb on 2005-12-16
It is wise to restrict samba access to your local subnet.

---

### Post by titaniumlou on 2005-12-17
Hi, I'm having trouble getting anonymous directories and directory browsing working.

Here is my smb.conf:
```


[global]
   workgroup = The_Hood
   netbios name = Titanium
   server string = 
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

   security = user
   encrypt passwords = true
   passdb backend = tdbsam guest
   obey pam restrictions = yes
   guest account = nobody
   invalid users = root

   guest ok = yes
   restrict anonymous = no
   protocol = LANMAN2

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=8192 SO_SNDBUF=8192

[share]
   comment = Share
   path = /home/user/share
   browsable = yes
   public = yes
   writable = no


```

I created a user with "smbpasswd -a username" and I can log in with that username and get to the share but I'm not sure what I'm missing in order to get anonymous access...

Plus I noticed that my passdb backend line is different from yours, and also I don't have a smbusers file on my machine...

Thanks in advance!

{edit}
I got mine working by putting this line in:
map to guest = bad user

---

### Post by arsya on 2005-12-18
So, davidsrsb,

Could you tell us how you can do "Restrict samba access to your local subnet."?

Thanks in advance...

---

### Post by titaniumlou on 2005-12-18
You should be able to do that with these lines:
hosts allow = 192.168.1.
hosts deny = *

You can find more in the smb.conf man page

---

### Post by davidsrsb on 2005-12-19
I have
hosts allow = 192.168.0.  127.
to avoid shutting out localhost

---

