---
title: "Problem printing larger files with samba (NT_STATUS_DISK_FULL)"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by will-o-the on 2009-01-26
While printing from ubuntu 8.04 clients hardy on a printer connected via samba I have the following problem:

Prining files larger then ca 2MB doesn't work following error occurs in the cupsd-errorlog:

Error writing spool: NT_STATUS_DISK_FULL
Call timed out: server did not respond after 10000 milliseconds closing remote
(/usr/lib/cups/backend/smb) stopped with status 1!

Small files are printed fine and it seems to make no difference which programm I use

When I connect the printer directly to one of the ubuntu clients everything works fine with the same driver and configuration.

The printer is a KyoceraMita FS-1920 and is connected to an Iomega NetworkStorecenter. Local and remote harddisks have lots of free diskspace.

---

