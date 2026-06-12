---
title: "samba/backuppc error: NT_STATUS_CONNECTION_RESET"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by tigerstripedcat on 2011-04-12
I am getting the following error from backuppc when trying to backup a windows7 machine from my ubuntu machine(though I believe this error comes directly from samba):

```
[ skipped 44618 lines ]
Error reading file \medSchool\body\dissectionimages\practice.pptx : NT_STATUS_CONNECTION_RESET
Didn't get entire file. size=272456645, nread=126584640
```

The backup occurs fine for *hours* but eventually I get this NT_STATUS_CONNECTION_RESET error.  I have purged and reinstalled samba/backuppc, I have removed my wins setup (not sure if that's relevant), and I have checked permissions.  As I said it seems to work fine for a while, but then stops.  This seems to be a problem with the windows machine, but I'm not completely sure.  What would cause the connection to reset after working so long.

Thanks
TSC

---

### Post by capscrew on 2011-04-12
> **tigerstripedcat said:**
> I am getting the following error from backuppc when trying to backup a windows7 machine from my ubuntu machine(though I believe this error comes directly from samba):

```
[ skipped 44618 lines ]
Error reading file \medSchool\body\dissectionimages\practice.pptx : NT_STATUS_CONNECTION_RESET
Didn't get entire file. size=272456645, nread=126584640
```

The backup occurs fine for *hours* but eventually I get this NT_STATUS_CONNECTION_RESET error.  I have purged and reinstalled samba/backuppc, I have removed my wins setup (not sure if that's relevant), and I have checked permissions.  As I said it seems to work fine for a while, but then stops.  This seems to be a problem with the windows machine, but I'm not completely sure.  What would cause the connection to reset after working so long.

Thanks
TSC

If either of the systems uses DHCP and the DHCP lease is renewed the the connection will be broken and not reset.  I think this is on the Samba side.  The samba server should not use DHCP (or reserved) addressing.

---

### Post by tigerstripedcat on 2011-04-12
I don't think this is the problem. DHCP leases last a matter of days.  Even if they wernt, the problem is so consistent (happens every time) that the chance that I'm hitting the renewal every time is vanishingly small.  Also I never experience any other samba related issues when this occurs.

---

