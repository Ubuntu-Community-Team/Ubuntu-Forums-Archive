---
title: "Samba and windows 7 Access Denied on Write"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by CheresZabor on 2010-09-10
Hello, 
I have been having problems with Samba sharing from my Ubuntu-Server to all of my Windows 7 machines. 

All of the machines are able to access the samba shares however when i try to write to these shares i get a "Access Denied" error. This only happens under windows 7, my Ubuntu laptop easily writes to these shares. 

Any suggestions? 

PS My permissions are read/write to all

---

### Post by chapado on 2010-09-13
I'm having the same problem. I've added a user "chapado" and given it a password with passwd, smbpasswd, chowned the directory/files to that user and even chmodded to 777. When I try to rename a file Windows gives me a "You require permission from ADVENTURE\chapado to make changes to this file".

This is how I have the share set up:
```

[library]
        path = /library
        read only = no
        create mask = 660
        directory mask = 770
        writeable = yes

```

I don't know what I'm missing, according to all the "Setup samba" guides I've read this should be it working.

Samba's log says I'm authenticating as the correct "chapado" user:
```

[2010/09/14 00:19:13,  1] smbd/service.c:1063(make_connection_snum)
  chapado-pc (192.168.1.244) connect to service sambashare initially as user chapado (uid=1002, gid=1002) (pid 7586)

```

---

### Post by Sameer Sirdeshpande on 2012-05-24
I'm having the same issue trying to connect from Win7 to latest version of samba on 12.04 LTS. I'm able to map the samba shared folder as a Windows drive letter but I'm not able to write to the samba folder -- I get "Access denied".

/etc/samba/smb.conf:
---
hosts allow =

[share]
comment = Name of Share
path = /srv/samba/share
browsable = yes
guest ok = yes
read only = no
create mask = 755
hosts allow =
---

Any thoughts on this? Thanks - Sameer

---

### Post by Morbius1 on 2012-05-24
Without knowing how you set up the users or how you set up the target folder I would guess this is a Linux permissions problem not a samba problem.

If you created /srv/samba/share it probably has permissions of owner=root and perms=755. Only root can write to the folder and everyone else can only read. One way out of this is:
```
sudo chmod 0777 /srv/samba/share
```

---

