---
title: "Giving up on Networking and CUPS -"
date: 2006-05-31
forum: Networking &amp; Wireless
---

### Post by pizzipie on 2006-05-31
HELP! HELP! HELP!   I have been trying to get network printers to work for ten days. One computer lost all its desktop so I re-installed breezy on the other one Now sees no printers.

I am trying to get a printer to work on one computer. Here is what I did.

1. In Systems=>Administration=>Printers=>local printer=>use detected printer it says NO PRINTERS DETECTED.

2. I removed ALL CUPS Software I could see.

3. In Systems=>Administration=>Printers it says THE CUPS SERVER COULD NOT BE CONTACTED.

4. In System=>Administration=>Device Manager I find Stylus Printer ... USB Interface.

SO, there is a printer detected. But I apparantly am in a catch 22 situation. I am about ready to reinstall Breezy on this computer also !!

Can anyone help me get this printer to work before I get drastic ??

Thanks for your help.

---

### Post by Boelcke on 2006-06-01
I have been struggling to share a printer myself.
([http://www.ubuntuforums.org/showthread.php?t=180342&page=2](http://www.ubuntuforums.org/showthread.php?t=180342&page=2))
Note that I'm pretty much a N00b, but:

I've found that while I'm messing around with the CUPS configuration files (cupsd.conf and client.conf, if I make it really bad, I also won't get the Administration, Printers window to come back up.  This is regardless of any local printers I might have attached.

I'd suggest trying to restore those .conf files back to the way they were, along with any other CUPS related stuff you might have torn out.  Then, you should be able to get that Printers window back up, and go through the normal, non-networked, add a printer routine.

---

### Post by pizzipie on 2006-06-05
[quote=Boelcke]I have been struggling to share a printer myself.
([http://www.ubuntuforums.org/showthread.php?t=180342&page=2]("http://www.ubuntuforums.org/showthread.php?t=180342&page=2"))
Note that I'm pretty much a N00b, but:

I've found that while I'm messing around with the CUPS configuration files (cupsd.conf and client.conf, if I make it really bad, I also won't get the Administration, Printers window to come back up.  This is regardless of any local printers I might have attached.

I'd suggest trying to restore those .conf files back to the way they were, along with any other CUPS related stuff you might have torn out.  Then, you should be able to get that Printers window back up, and go through the normal, non-networked, add a printer routine.[/quote] 
Thanks Boelcke. I received some help from 'connellr' See No 27 in 'networking' doc #30920. This has given me renewed hope. I am also a glutton for punishment so am going to try this on 'dapper'

rp

---

