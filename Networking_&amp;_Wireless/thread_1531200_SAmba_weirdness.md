---
title: "SAmba weirdness"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by malcmail on 2010-07-14
Completely confused. The file /etc/samba/smb.conf reads as follows:-
In the global section:
 CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printcap name = cups
printing = cups   
security = share
browseable = yes
browsable = yes

In the printers section:
[printers]
   comment = All Printers
   
public = yes
   path = /var/spool/samba
#path = /tmp
   printable = yes
   guest only = yes
   read only = no
   create mode = 0700
use client driver = yes
browseable = yes
browsable = yes

Then I do service smbd restart. All is well. But testparm on the same file returns:

[printers]
    comment = All Printers
    path = /var/spool/samba
    read only = No
    create mask = 0700
    guest only = Yes
    guest ok = Yes
    printable = Yes
    use client driver = Yes
    browseable = No
    browsable = No

One question - why?

Sorry dont know the tag for putting the code in properly either :-s

---

