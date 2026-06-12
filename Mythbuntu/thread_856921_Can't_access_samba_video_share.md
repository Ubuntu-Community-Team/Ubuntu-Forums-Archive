---
title: "Can't access samba video share"
date: 2008-07-11
forum: Mythbuntu
---

### Post by Lindsay.Mathieson on 2008-07-11
Stock install of mythbuntu + weekly fixes. 

I can't access my Music, Pictures and Videos shares via samba. Can access the Recordings one though.


This used to work but stopped recently - haven't touched anthying so I'm guessing an issue in weekly fixes?

I get this entry in the samba logs:

```
[2008/07/12 13:52:49, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/07/12 13:52:49, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

```

My smb.conf

```
[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share

[recordings]
comment = TV Recordings
path = /var/lib/mythtv/recordings
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[videos]
comment = Videos
path = /var/lib/mythtv/videos
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

```

I'm guessing Recordings is ok because force user/group = Nobody


Any suggestions?

---

### Post by Lindsay.Mathieson on 2008-07-13
Bump :( Has anyone even run in to this problem before? I've found stuff via google that implies a problem with the builtin users but non of the suggested fixes worked.

---

### Post by blackoper on 2008-07-14
install and use webmin to setup and modify your samba shares.

---

### Post by Lindsay.Mathieson on 2008-07-14
Thanks blackoper, I did have a look at webmin but i prefer to stick to packages and webmin is heavily depreciated. I tried another admin packages (echo?) and it completely hosed my network setup :(

I actually made some progress over the weekend - I think it was wine that broke things. Following some instructions I removed samba and samba-common. Oddly it uninstalled wine as well - must be a dependancy there. Once I reinstalled everything was ok.

Once I get a chance I'll reinstall wine and see if that breaks things.

---

### Post by Thuffir on 2008-08-08
> Once I get a chance I'll reinstall wine and see if that breaks things.

I think it was definately WINE. I had the same problem, and after deinstalling WINE and reinstalling SAMBA it worked again for me.

---

### Post by Lindsay.Mathieson on 2008-08-08
Agreed. I tested some more and someone else on the mythtv list ran into the same problem. The culprit appears to be winbind which is installed along with wine. If you just kill the winbind daemon evrything is fine.

---

### Post by muranternet on 2009-08-13
I have the same issue, samba share that was working up until 2 days ago mysteriously disappeared from the local workgroup, although the box was pingable, MythWeb worked, and I could shell into the box from the LAN.  I do not use Wine.  Will try a reinstall of Samba and see if it works.  I'll look for Winbind just in case but again I never use Wine on the appliance so I doubt it's there.

Update:  Didn't work.

---

