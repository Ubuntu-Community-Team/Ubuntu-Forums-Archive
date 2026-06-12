---
title: "[SOLVED] Sharing a Windows XP Printer"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by purplepaint on 2008-12-18
I have a HP Deskjet 710C connected to a desktop running Windows XP, which is connected via an ethernet cable to my wireless router.  My Ubuntu laptop is connected to the router via its wireless connection, and that's how I connect to the internet (sorry for spelling all this out, but I know nothing about networking other than how to plug in a router and connect to it with a laptop!).

I understand that it is possible to share my printer, through Windows, with my laptop to allow me to print directly from it (at the moment, I have to save files, such as .odt documents, onto a USB flash drive and then transfer them to the Windows desktop for printing).

Have I heard correctly (I assume the Windows machine has to be switched on to make this work)?

---

### Post by cariboo on 2008-12-18
To answer your last question first, yes of course the XP computer has to be turned on.

Your HP printer is well supported so you shouldn't have any problem setting it up. I Windows right-click on your printer and select sharing, and set it up. Next go to System-->Administration-->Printing and click new printer. In the Printer Configuration window select Windows Printer via Samba, and just follow the prompts from there.

Jim

---

### Post by horacle on 2008-12-18
I have also a minilan in my house, 2 dualbox machines, the one with the printer is xp/fedora, the other is xp/ubuntu... the thing is, when in the host fedora is running, I can print with no problems from ubuntu, but when the host is xp, I cant. The xp host is configured to share printers and folders, as I can print from the xp/ubuntu while working with xp. 

In the office I have an ubuntu box sharing a printer (its a large lan with a few machines sharing printers and a couple of ip printers, just 1 linux box) and all the xp boxes around can use the printer, but in ubunto I can print only with the local printer or the ip printers, not with the printers shared by xp hosts. I dont know whats wrong with either os.

---

### Post by purplepaint on 2008-12-18
> **cariboo907 said:**
> To answer your last question first, yes of course the XP computer has to be turned on.

Your HP printer is well supported so you shouldn't have any problem setting it up. I Windows right-click on your printer and select sharing, and set it up. Next go to System-->Administration-->Printing and click new printer. In the Printer Configuration window select Windows Printer via Samba, and just follow the prompts from there.

Jim

Thanks for the reply.  Turns out I'd worked it out for myself, I just had to prevent my firewall from blocking Samba.

---

