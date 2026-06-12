---
title: "winbind name resolution fails after samba install"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by axe87 on 2010-09-01
Having got name resolution fixed using winbind and working perfectly I decided to share the printer on my new ubuntu box and therefore installed samba.

Result: name resolution no longer works, even after rolling back the samba installation.

I get the following error when trying to access the windows network from nautilus:

"Unable to mount location: Failed to retrieve share list from server"

and command line name resolution now fails.

In log.winbindd-idmap I'm seeing the following errors.

> [2010/09/01 14:02:05,  1] winbindd/idmap.c:438(idmap_init_passdb_domain)
  Could not init passdb idmap domain
[2010/09/01 14:02:05,  1] winbindd/idmap_tdb.c:214(idmap_tdb_load_ranges)
  idmap uid missing
[2010/09/01 14:02:05,  0] winbindd/idmap_tdb.c:287(idmap_tdb_open_db)
  Upgrade of IDMAP_VERSION from -1 to 2 is not possible with incomplete configuration
[2010/09/01 14:02:05,  1] winbindd/idmap.c:321(idmap_init_domain)
  idmap initialization returned NT_STATUS_UNSUCCESSFUL
[2010/09/01 14:02:06,  0] winbindd/idmap.c:201(smb_register_idmap_alloc)
  idmap_alloc module tdb already registered!
[2010/09/01 14:02:06,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module passdb already registered!
[2010/09/01 14:02:06,  0] winbindd/idmap.c:149(smb_register_idmap)
  Idmap module nss already registered!

I've looked at a number of threads on the nautilus error message and can't find a resolution that works.

It was all going so well in making the leap from windows to ubuntu...actually I'm very impressed how smoothly it went...I just need to get over this hurdle.

---

### Post by axe87 on 2010-09-02
Well it seems that the problem was in the smb.conf installed with Samba / GADMIN-SAMBA and then left behind after I removed Samba.

I hadn't spotted that the ip address range in the interfaces parameter was wrong:

```
interfaces = 127.0.0.1/8 192.168.0.0/24
```

instead of 

```
interfaces = 127.0.0.1/8 192.168.2.0/24
```

Hmm, never would've got that from the error messages.

---

