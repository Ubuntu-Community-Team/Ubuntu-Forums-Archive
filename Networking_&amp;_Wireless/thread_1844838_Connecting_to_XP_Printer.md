---
title: "Connecting to XP Printer"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by Orcris on 2011-09-15
I'm using Kubuntu 11.04, and the only printer on my network is connected to an XP machine. I don't have a home server. The printer is an Epson NX410, and it is set up to share with UNIX. How do I connect to it using Kubuntu?

---

### Post by SeijiSensei on 2011-09-16
If you share the printer normally in Windows, you can use the smb:// method in CUPS to connect to it.  I'd make sure the XP machine has a fixed IP address, then use smb://ip.addr.xp.machine/printersharename to connect.

Use System Settings > Printer Configuration > New Printer > New Network Printer.  It may detect the printer automatically.  If not, choose "Windows Printer via SAMBA" from the list after automatic detection times out.

---

### Post by Orcris on 2011-09-18
I did that and found my printer, but the driver for it wasn't on the list. The driver for an Epson NX410 isn't on the list.

---

