---
title: "Samba Guest Share and password Protected Share"
date: 2010-09-24
forum: Networking &amp; Wireless
---

### Post by conoral11 on 2010-09-24
Hi there,

I'm trying to setup two samba shares on ubuntu server 10.04.1 lts x64

The first is a Read-Only share for windows users that doesn't require a password. This i've managed to do so far.

The second is a Password protected Upload share. So far I am able to have both shares (which access the same directory) but am unable to log in to the pass word protected share.

I know i'm not doing things quite right, and would like a little bit of help

The smb.conf file is the default ubuntu file with these added shares:

```
[NAS]
Comment = Network Attached Storage
path = /media/RAID/NAS
browseable = yes
writeable = no
guest ok = yes
guest account = nobody
security = share

[NAS-UPLOAD]
comment = NAS Upload Share
path = media/RAID/NAS
browseable = yes
writeable = yes
```

The [NAS] share works as intended, the [NAS-UPLOAD] Share asks for a password but will never let me log in.

The user has been added using 

```
smbpasswd -a nasuser
```

nasuser owns the /media/RAID/NAS directory.

Any help would be greatly appreciated!

Conoral11

---

### Post by luvshines on 2010-09-27
Are the paths which you intend to share same ??

/media/RAID/NAS in [NAS]

AND

media/RAID/NAS in [NAS-UPLOAD]

NAS-UPLOAD doesn't start with /, is that a typo ?

---

### Post by rcayea on 2010-09-27
Have you run the following command?

smbpasswd -e username

---

### Post by Crazedpsyc on 2010-09-27
Theres a gui to make that easier. Just run system-config-samba to get it. If it's not installed bash should tell you how to install it

---

### Post by Morbius1 on 2010-09-27
If there is a question as to whether "nasuser" is in the samba user database run the following command:
```
sudo pdbedit -w -L
```You'll get an output that looks something like this: 
>  [COLOR=Blue]**nasuser**[/COLOR]:1001:XXX...:A3B....:[[COLOR=Blue]**U**[/COLOR]          ]:LCT-4C....:If you don't see nasuser or if the U is a DU then you either don't have a samba password for nasuser ( or you don't have a local login user named nasuser ) or it has been disabled.

The "smbpasswd -e nasuser" suggested by rcayea will re-enable it but it shouldn't have been necessary since "smbpasswd -a" both adds and enables a new samba user automatically.

As a side note I'm fairly certain samba is ignoring these parameters in the share that works:
> guest account = nobody
security = share  If you do a "testparm -s" it should give you a "Global parameter security found in service section" or words to that effect.

---

### Post by conoral11 on 2010-10-04
Thank you very much for your help.

I solved my situation by removing the secuirty parameters from the share definitions.

I changed the global defintion for secuirty to share, and set the NAS-UPLOAD share to include valid users.

Now it all works.

Here my code for anyone else who has been having issues

```
[NAS]
comment = Network Attached Storage
path = /media/RAID/NAS
browseable = yes
writeable = no
guest ok = yes

[NAS-UPLOAD]
    comment = NAS Upload Share
    path = /media/RAID/NAS
    browseable = yes
    valid users = nasuser
    writable = yes
```

All the best

Conoral11

---

