---
title: "linux machine cannot connect to samba printer"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by linuxcss on 2013-03-04
running xubuntu 12.10 on both linux samba server and linux client

linux client machine cannot connect to samba printer served via linux server

have usb printer on linux machine serving via samba

testparm  shows this:
--------------------
[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---------------

smbtree shows:

\\CWX4A               cwx4a server (Samba, Ubuntu)
        \\CWX4A\HP-LaserJet-5M     Hewlett-Packard HP LaserJet 5M

a window's machine can print via samba to \\CWX4A\HP-LaserJet-5M

when adding a printer from a Linux Client and browsing then for the LaserJet 5M
it sees it but no matter what user name and pasword I give it fails to allow connection

says "Print Share Inaccessible" 

somebody got an answer to resolve this?

---

