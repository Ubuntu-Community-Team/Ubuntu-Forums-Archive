---
title: "Sharimg external D: with samba"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by sojakob on 2010-08-26
Hi guis!

I've been expeerimenting with ubuntu for some time and I am thrilled. Though, I have a problem with samba...
That is, we have a media station [ubuntu] and some PC&#347; [mainly paywareOS] on either Nautilus'es or real samba shares. I've been trying to figure out how to share files on an external D: but Samba's nor Nautilus share seems to be able to have acces.

(I'm sorry for my poor english - and i have searched before posting!)

Thanks in advance for any [realy any] reply

-sojakob

---

### Post by Morbius1 on 2010-08-26
> on either Nautilus'es or real samba shares.
Sorry, I'm kind of sensitive about this but Nautilus-shares are "Real Samba Shares". It's been part of Samba (where it's called usershares ) for years.

Anyway, we need more information:

Is this "external D" connected to an Ubuntu machine?

Is it formatted in NTFS or FAT32 or some linux filesystem.

Post the output of the following commands so we can see how your shares are set up:
```
net usershare info
```
```
testparm -s
```

---

### Post by sojakob on 2010-08-27
Thanks a lot.

The drive is formated in FAT32.

```
net usershare info
```Gives:
```
[film]
path=/home/[NAME]/Film
comment=
usershare_acl=Everyone:R,
guest_ok=n

[musik]
path=/home/[NAME]/Musik
comment=
usershare_acl=Everyone:R,
guest_ok=n

``````
testparm -s
```Gives:

```

Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Processing section "[Film]"
Processing section "[Musik]"
Processing section "[Hentede filer]"
Processing section "[TURK-downloadF]"
Processing section "[TURK-Film]"
Processing section "[TURK-gamez]"
Processing section "[TURK-musik]"
Processing section "[TURK-programs]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    netbios name = [sharename]
    server string = 
    null passwords = Yes
    username map = /etc/samba/smbusers
    syslog only = Yes
    announce version = 5.0
    name resolve order = hosts wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = CUPS
    wins support = Yes

[print$]
    path = /var/lib/samba/printers
    write list = root
    read only = No
    create mask = 0664
    directory mask = 0775
    guest ok = Yes

[printers]
    path = /tmp
    guest ok = Yes
    printable = Yes
    browseable = No
    browsable = No

[MyFiles]
    path = /home/samba/
    force user = [NAME]
    force group = [NAME]
    read only = No
    create mask = 0644

[Film]
    path = /home/[NAME]/Film
    guest ok = Yes

[Musik]
    path = /home/[NAME]/Musik
    guest ok = Yes

[Hentede filer]
    path = /home/[NAME]/Hentede filer
    guest ok = Yes

[TURK-downloadF]
    path = /media/TURK/downloadF
    guest ok = Yes

[TURK-Film]
    path = /media/TURK/Film
    guest ok = Yes

[TURK-gamez]
    path = /media/TURK/gamez
    guest ok = Yes

[TURK-musik]
    path = /media/TURK/musik
    guest ok = Yes

[TURK-programs]
    path = /media/TURK/programs
    valid users = [USER1, USER2...]
    browseable = No
    browsable = No


```TURK-*** are the folders I'm having trouble sharing.

---

### Post by Morbius1 on 2010-08-27
Let's assume that the login user to the Ubuntu box is named: morbius.

When the external drive is turned on it will be mounted to /media/TURK with owner = morbius and permissions set to 0700. Morbius can read and write to the drive ( the "7" part ) but everyone else will have no access at all ( the "0" part ). You told samba to allow guests but it can't override linux permissions.

You can fix that in smb.conf by adding the following line to each of the "TURK" shares:
```
force user = morbius
```For example, this:
> [TURK-downloadF]
    path = /media/TURK/downloadF
    guest ok = Yes
Becomes this:
> [TURK-downloadF]
    path = /media/TURK/downloadF
[COLOR=Blue]force user = morbius[/COLOR]
    guest ok = YesThen restart samba:
```
sudo service smbd restart
```

---

