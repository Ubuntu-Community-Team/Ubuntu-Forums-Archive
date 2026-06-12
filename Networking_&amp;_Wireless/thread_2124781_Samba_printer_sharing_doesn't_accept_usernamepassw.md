---
title: "Samba printer sharing doesn't accept username/password, but file server works"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by MichiGreat on 2013-03-12
**Hello!**

My system is running Xubuntu 12.04 x64 und I have Samba installed. Access to the file server works fine. But if I try to access shared printers on that system using another Xubuntu 12.04 (but x86, but that shouldn't matter), the shared printers are listed but accessing them doesn't work: The client asks for username and password again and again, no matter what I enter. Even the root account doesn't work (system actually has a root account). There are no relevant messages in /var/log/samba/* nor in the syslog.

The relevant sections in smb.conf look like this:

```

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   public = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

```

Any ideas how I could solve or trace this problem?

Printing using IPP works, but I want to use Samba because it is supposed to work via IPv6 too.

Best regards

*Michael*

---

