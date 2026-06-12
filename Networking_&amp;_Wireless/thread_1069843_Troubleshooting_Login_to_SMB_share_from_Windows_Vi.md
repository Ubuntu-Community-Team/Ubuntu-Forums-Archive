---
title: "Troubleshooting Login to SMB share from Windows Vista"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by devehf on 2009-02-14
I have been running Samba for some time and have been able to copy files from my Ubuntu box to our family's Windows laptops from work and school. I just got a new work laptop that is totally locked down so I can't create any shares on it.

I decided to share a directory on my Ubuntu box so I could copy files to it from our laptops. I added the share in smb.conf and I can see it in Windows Explorer, but when I try to connect and authenticate with my Ubuntu username and password, Windows inserts the Windows domain in front of the username. How can I specify in the Windows authentication dialog box that I want to log in as a user on the Ubuntu computer? 

Do i need to set up a user mapping file on the Ubuntu machine so that Samba interprests any domain user as a local Ubuntu user?

Thanks in advance.

---

### Post by H4ST3 on 2009-03-29
I am having the same problem. Would one of you networking wiz's care to share a solution? :)

---

### Post by Mchl on 2009-04-11
I also have problem with this... I'm fairly inexperienced with Linux in general and Ubuntu in particular and I just have no clue...

---

### Post by FrankT-Qc on 2009-04-11
Windows will insert the domain name in front of your user name in the dialog box, but when it comes to exchanging the L/P, it should not be make a difference so I'd look somewhere else for errors.

A few things : first, you might want to make sure your passwords are synchronized between Samba and your server... try "man smbpasswd".

Second, you want to make sure that the user you want to use for Samba login has access permissions to the share on the server (not in smb.conf but in the filesystem itself...)

Can you post your smb.conf  ?

Also, if you try logging in this very share with the same L/P from any other box, do you have the same problem ? You could try something like this on the samba server

```
smbclient '\\localhost\share' -U TheUser -d=5
```

Where "TheUser" is the name you want to use from your windows machine.

Note that "-d=5" is the level of verbosity of smblcient... 0 won't say anything, 10 will flood you with information... try something between the 0 and 10 until you find what's wrong

I you go to /var/log/samba , you might also find pretty good hints in the logs (phrases like "User ABCD : Login failed: File access denied ...")

---

### Post by Mchl on 2009-04-11
Ok. So it seems it was probably a samba user password issue. I reentered user password in samba administrator gui and I am now able to connect.
Many thanks!

---

### Post by devehf on 2009-05-24
I'm still not having luck. I can't make sense of the errors. How do I access the Samba GUI? Thanks!

When I try this:
```
smbclient '\\localhost\Music' -U TheUser -d=5
```

Everything looks fine until this happens:
```
Client started (version 3.0.28a).
Opening cache file at /var/run/samba/gencache.tdb
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
gencache_init: Opening cache file /var/run/samba/gencache.tdb read-only.
sitename_fetch: No stored sitename for 
no entry for localhost#20 found.
resolve_lmhosts: Attempting lmhosts lookup for name localhost<0x20>
startlmhosts: Can't open lmhosts file /etc/samba/lmhosts. Error was No such file or directory
```

The log.winbindd-idmap has this error:
```
[2009/05/24 21:30:15, 1] nsswitch/idmap_tdb.c:idmap_tdb_alloc_init(397)
  idmap uid range missing or invalid
  idmap will be unable to map foreign SIDs
[2009/05/24 21:30:15, 0] nsswitch/idmap.c:idmap_alloc_init(750)
  ERROR: Initialization failed for alloc backend, deferred!
```

And then after the password entry when this happens:
```
SPNEGO login failed: Logon failure
session setup failed: NT_STATUS_LOGON_FAILURE

```

The log.wb-HOST has this error:
```
[2009/05/24 21:30:15, 0] nsswitch/winbindd_passdb.c:sid_to_name(130)
  Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend
```

The log.HOST has this error:
```
[2009/05/24 21:30:15, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2009/05/24 21:30:15, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
```

Here's the share from my smb.conf:
```
[Music]
	path = /home/TheUser/Music
	read only = no
```

---

