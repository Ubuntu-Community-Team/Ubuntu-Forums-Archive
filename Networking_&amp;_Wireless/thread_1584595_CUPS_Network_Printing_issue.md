---
title: "CUPS Network Printing issue"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by Deenoe on 2010-09-29
Good day everyone, 

I currently have set up a Linux workstation with the latest Ubuntu version installed. 
I have a HP Laserjet P1005 connected to it by USB, which I have shared using CUPS.

Two clients use this printer ; a Mac and a Windows 7 client. The Mac computer has no problem sending PDFs to the CUPS server, whereas the Windows client has some problems.

What I have noticed is that it takes minutes before the file from the Windows client actually *gets* to the spool. Let's say the file is being sent, it doesn't show up in the Jobs in CUPS before 10-15 minutes. We're talking about moderately sized PDFs.

I doubt it's a connectivity issue with the Windows client, but I was wondering, is there any way to speed things up ? Is Samba the solution ? 

Thanks,
-D

---

### Post by Joshun on 2010-09-29
You could try samba, the printer should show up as print$. An article about samba printing can be found here: [http://www.samba.org/samba/docs/using_samba/ch10.html](http://www.samba.org/samba/docs/using_samba/ch10.html)
more info: [http://wiki.samba.org/index.php/Samba_as_a_print_server]("http://wiki.samba.org/index.php/Samba_as_a_print_server#Using_a_printer_connected_to_another_Samba_server"):popcorn:

---

