---
title: "Help with network drive in Windows XP"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by User X on 2010-02-19
I have set up my Ubuntu 9.10 installation to share a few folders over the network with my windows machines.  When I go to map the network drive in XP I can browse to the Ubuntu machine, see the folders I am sharing, and choose them to set up the path.  I accept the network drive settings and I am given the message, "cannot connect to network drive: more info is available".  What is this all about???

---

### Post by Morbius1 on 2010-02-19
From the Ubuntu machine please post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

From the WinXP machine please post the output of the following command:

Open **Command Prompt** ( not run but Command prompt )
Type **net view**

---

### Post by User X on 2010-02-19
net usershare info:
```

[music]
path=/home/userx/Music
comment=
usershare_acl=Everyone:F,
guest_ok=n

[pictures]
path=/home/userx/Pictures
comment=
usershare_acl=Everyone:F,
guest_ok=n

[movies]
path=/home/userx/Movies
comment=
usershare_acl=Everyone:F,
guest_ok=n

[videos]
path=/home/userx/Videos
comment=
usershare_acl=Everyone:F,
guest_ok=n

```

testparm -s:
```

Load smb config files from /etc/samba/smb.conf
Processing section "[recordings]"
Processing section "[videos]"
Processing section "[music]"
Processing section "[pictures]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	workgroup = PROVINCEAUTO
	server string = %h server (Samba, Mythbuntu)
	security = SHARE
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d

[recordings]
	comment = TV Recordings
	path = /var/lib/mythtv/recordings
	force user = nobody
	force group = nogroup
	create mask = 0777
	directory mask = 0777
	guest ok = Yes

[videos]
	comment = Videos
	path = /var/lib/mythtv/videos
	force user = mythtv
	force group = mythtv
	read only = No
	create mask = 0660
	directory mask = 0770
	guest ok = Yes

[music]
	comment = Music
	path = /var/lib/mythtv/music
	force user = mythtv
	force group = mythtv
	read only = No
	create mask = 0660
	directory mask = 0770
	guest ok = Yes

[pictures]
	comment = Pictures
	path = /var/lib/mythtv/pictures
	force user = mythtv
	force group = mythtv
	read only = No
	create mask = 0660
	directory mask = 0770
	guest ok = Yes

```

net view:
```

\\ACHILES
\\HTPC                HTPC server (Samba, Mythbuntu)
The command completed successfully.

```

Thanks for any help!

---

### Post by Morbius1 on 2010-02-20
There are two completely different and separate methods of sharing files in Ubuntu. "Classic Samba" which defines shares in smb.conf , and "Nautilus-share" which defines shares in /var/lib/samba/usershares.

You are using both methods at the same time. They are pointing to different folders but the share names are identical, For example:

Nautilus-share:
> [music]
path=/home/userx/Music
comment=
usershare_acl=Everyone:F,
guest_ok=nClassic Samba:
> [music]
    comment = Music
    path = /var/lib/mythtv/music
    force user = mythtv
    force group = mythtv
    read only = No
    create mask = 0660
    directory mask = 0770
    guest ok = Yes
They're pointing to two different target folders but they have the same share name. Nautilus share denies guest access, Classic samba allows it. You need to change one set of share names so they don't match with the other. Change "music" to "music1" or "music-myth" or something other that "music"

---

