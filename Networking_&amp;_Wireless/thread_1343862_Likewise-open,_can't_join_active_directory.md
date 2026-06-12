---
title: "Likewise-open, can't join active directory"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by rick71 on 2009-12-02
I am using 9.04, fully updated.

I have like-wise open and likewise-open gui installed.

When I use the cli to join the domain I get the following:

```

[2009/12/02 09:53:03,  0] utils/net_ads.c:ads_startup_int(493)
  ads_connect: No logon servers
Failed to contact DC when trying to synchronize local system clock!
None of the domain controllers listed in DNS could be contacted, or there are no DCs listed in DNS.

Error: Unable to join domain [code 0x0008000e]

Domain join operation failed to create the computer account in Active
Directory. Common causes are a bad administrator password, a bad OU name, or an
existing computer account without modification permissions.

```

I have a room full of Windows XP clients all logging into the via Active Directory on the Domain Controller. The Domain Controller and DNS server are the same machine.

Anyone have any idea how I might be able to fix this?

---

### Post by rick71 on 2009-12-13
bump

---

### Post by fatality_uk on 2009-12-15
Dozens of reasons there! I would suggest that most likely is a BAD OU or a machine with the same name on there. Try renaming your machine and make sure that you use a FDQN.

---

### Post by rick71 on 2009-12-17
> **fatality_uk said:**
> Dozens of reasons there! I would suggest that most likely is a BAD OU or a machine with the same name on there. Try renaming your machine and make sure that you use a FDQN.

I have renamed it. I have tried to join with 2 Ubuntu machines and 2 opensuse machines. None have joined.

Might Services for Unix need to be installed on the W2K3 DC?

---

