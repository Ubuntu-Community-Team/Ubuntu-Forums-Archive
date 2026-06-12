---
title: "Cannot connect to SMB shares as guest from Windows with security=user"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by 8086 on 2010-10-25
I want to achieve two things with my Samba setup:
1. Have some general shares that one does not need a password to access.
2. Access my home folder using a username and password.

Getting #1 to work when using share level security was quite painless, but my problems started when trying to achieve goal #2.
I have used ```
smbpasswd -a my_login
``` for the relevant account.

**More on the problem :**
The following works from any Ubuntu command prompt:
```
smbclient //filserver/filmarkiv -U guest
```

But when trying to connect to the fileserver using Windows I can not connect. Ideally I should not get a command prompt here at all ...

[IMG]http://dl.dropbox.com/u/514315/diskusjonsfora/not%20correct.PNG[/IMG]

**My smb.conf**:
```
[global]
workgroup = LB8
netbios name = timbuktu
security = user
socket options = TCP_NODELAY

[musikkarkiv]
comment = Her ligger masse flac og mp3
path = /mnt/data/musikkarkiv
read only = Yes
guest ok = Yes
case sensitive = True

[filmarkiv]
comment = Her ligger en del serier og filmer
path = /mnt/data/video
read only = Yes
guest ok = Yes

[delt]
comment = Her kan man dele musikk og film
path = /mnt/data/sambashare
read only = no
guest ok = Yes
force group = users
force user = smbklient

[homes] 
comment=Home directory for %S 
;path=/home/%u 
valid users = %S
;force user=%u 
writeable = yes 
browseable = no

```

---

### Post by Morbius1 on 2010-10-25
To the global section of smb.conf add the following line:
```
map to guest = Bad User
```
Then restart samba:
```
sudo service smbd restart
```

BTW, What have you done with the rest of your smb.conf?

---

### Post by 8086 on 2010-10-25
Thank you, that worked beautifully!

I am not quite sure what you mean by "the rest", but if you mean the default file I started from scratch after reading a bit at the SAMBA Howto. 

If you mean that I originally had a little bit different smb.conf that I edited soon after posting, it was because I solved one of my original problems that were caused by having "path=/home/%u " in the [homes] section.

---

### Post by luvshines on 2010-10-25
#2: For [homes], make sure you have /home/<user-name> directory available for the user you are trying to connect with. I don't think they will be created on-the-fly

---

