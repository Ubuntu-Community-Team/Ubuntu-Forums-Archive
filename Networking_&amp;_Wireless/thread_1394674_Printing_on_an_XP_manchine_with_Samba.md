---
title: "Printing on an XP manchine with Samba"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by 400killer on 2010-01-30
I am running ubuntu 9.04 with samba 4. I have successfully added my shared folder as a mapped network drive on the xp box. Also I have added my brothers MFC - 5840cn printer using the samba connection, it verifies and connects.  The problem I'm having is if I print anything to it, the X box will show it processing then printing the it will dissapear from the spooler.  It then shows up in the Brothers queue on the Xp box as a remote downlevel document and spools, then goes to printing. The printer display lights up on the printer. This is where it goes sidways. The queue then shows the doc printed and disappears from the queue, and the backlights on the display then go back out on the printer. I have no errors anywhere.  I can print from other windows boxes with out a problem to that printer, including this laptop booted into windows.  Has anyone run into this? Thanks ahead of time for any help. 

Heres the config enties for the smb.conf file:


    load printers = no
   printing = bsd
   printcap name = /dev/null
   printing = bsd
   printcap name = cups
   printer admin = @lpadmin

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

---

