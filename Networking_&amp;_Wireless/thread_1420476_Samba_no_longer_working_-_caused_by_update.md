---
title: "Samba no longer working - caused by update?"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by Another Monkey on 2010-03-03
I think an update or something has killed Samba on my Karmic box.  it can see Windows shares OK, but it no longer appears on the Windows network.  I have not changed my smb.conf for months, so something else has been modified.

Looking in the logs I can see the following in "log.winbindd-idmap" after restarting Samba
```
[2010/03/03 10:07:20,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/03/03 10:07:20,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/03/03 10:07:20,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/03/03 10:07:20,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/03/03 10:07:20,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/03/03 10:07:20,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/03/03 10:07:20,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/03/03 10:07:20,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/03/03 10:07:20,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/03/03 10:07:20,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/03/03 10:07:20,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/03/03 10:07:20,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL
[2010/03/03 10:07:20,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/03/03 10:07:20,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!
[2010/03/03 10:07:20,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/03/03 10:07:20,  0] winbindd/idmap_tdb.c:341(idmap_tdb_alloc_init)
  idmap will be unable to map foreign SIDs: NT_STATUS_UNSUCCESSFUL

[2010/03/03 10:07:20,  0] winbindd/idmap.c:589(idmap_alloc_init)
  ERROR: Initialization failed for alloc backend, deferred!
```

This is my smb.conf, as I say I have not changed it in months
```

[global]
	workgroup = linux-massive
	server string = Linux %h
#   wins support = no
	dns proxy = no
;	name resolve order = lmhosts wins host bcast

	security = user
;   encrypt passwords = yes
;   passdb backend = tdbsam
	obey pam restrictions = yes
	unix password sync = yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	pam password change = yes
	map to guest = bad user
	smb ports = 139

	usershare allow guests = yes
;    guest ok = no
;    guest account = nobody
	username map = /etc/samba/smbusers

[RelayPoint]
	comment = Relay Point
	path = /home/<user name>/RelayPoint
	writeable = yes
;    browseable = yes
	valid users = <user name>
```

All other networking seems fine (internet, Synergy+ etc) it's just sharing out to the Windows network that is broken.

I've been searching but can't find an answer - anyone any idea what this problem is and how to fix it?  Thanks.

---

### Post by Another Monkey on 2010-03-03
Just noticed something odd.  When I navigate to "Linux-Massive" in Nautilus, it jumps straight to showing me the shares from another PC (a Windows virtual image running on the Ubuntu host) rather than listing the PCs in the workgroup.

In Samba I just tried changing the workgroup name from "linux-massive" to "linux-test" and rebooting.  I can see that workgroup but it is not accessible from Nautilus.

I'm pretty sure something is goosed in Samba/winbind; but I don't fell I know enough tech detail to log a bug.

I am also seeing this in log.winbindd-idmap
```
[2010/03/03 11:26:55,  0] winbindd/winbindd.c:190(winbindd_sig_term_handler)
  Got sig[15] terminate (is_parent=0)
```

---

### Post by Another Monkey on 2010-03-04
Weird.  It seems to be working after the updates today (I was tired, I really didn't pay attention to what went in).
But with now changes, restarts or anything I can now browse to my Ubunut box from Windows.

I guess I will file this under PEBKAC.

---

### Post by freemant on 2011-10-27
I had the same problem. To fix it, make sure the following lines are NOT commented out:

```

   idmap uid = 10000-20000
   idmap gid = 10000-20000

```

---

