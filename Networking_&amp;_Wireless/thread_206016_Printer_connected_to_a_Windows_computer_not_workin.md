---
title: "Printer connected to a Windows computer not working with Ubuntu"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by MrPacane on 2006-06-29
I just configured my Ubuntu PC with my home network. Everything works well with the file sharing but I can't get my printer to work... (the printer is connected to a Windows computer)

I used Ubuntu's software to set up the printer on my machine. I thought it was going to work because both host and printer figured in the software's lists! But when I tried to print a test page, I could hear some noises coming from my printer but nothing came out of it... Then I saw that there was one job waiting in the printer's queue on the Windows computer (where the printer is connected). I came back to my Ubuntu PC and I checked if the job still figured but it didn't. I think the job was sent to the Windows computer (where the printer is connected) but it has never printed I don't know why...

Could someone help me please :roll: ?

By the way my printer is a HP PSC-1310.

---

### Post by DarkaOnLine on 2006-06-30
Hi MrPacane,
I have the same problem and i am trying to figure out how to fix this problem. If I will figure out I will tell you how. Good luck

---

### Post by DarkaOnLine on 2006-06-30
[QUOTE=DarkaOnLine]Hi MrPacane,
I have the same problem and i am trying to figure out how to fix this problem. If I will figure out I will tell you how. Good luck[/QUOTE]

Try this: [http://ubuntuforums.org/showthread.php?t=91001&highlight=windows+Network+printer](http://ubuntuforums.org/showthread.php?t=91001&highlight=windows+Network+printer)

---

### Post by DarkaOnLine on 2006-06-30
When you add the printer in Ubuntu,

   1. Choose “Network Printer” and “Windows Printer (SMB)”
   2. put your Workgroup in the Host field
   3. Put “guest@<host>/<printer>” in the Printer field (replacing <host> and <printer> with your host & printer names)

So, for example, if your Windows machine was called “Dozer” and your printer was called “LaserPrinter”, you would put “guest@Dozer/LaserPrinter”.

You should not need a name and password for the Windows machine for this to work.

---

### Post by DarkaOnLine on 2006-06-30
[QUOTE=DarkaOnLine]When you add the printer in Ubuntu,

   1. Choose “Network Printer” and “Windows Printer (SMB)”
   2. put your Workgroup in the Host field
   3. Put “guest@<host>/<printer>” in the Printer field (replacing <host> and <printer> with your host & printer names)

So, for example, if your Windows machine was called “Dozer” and your printer was called “LaserPrinter”, you would put “guest@Dozer/LaserPrinter”.

You should not need a name and password for the Windows machine for this to work.[/QUOTE]


More over you will need HP drivers. You can get them trom: [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

Download them. Tar it then go to the System ->Administration -> Printing.  Select your new printer in the Properties menu klic Drivers and the Install Drivers. Open your extracted folder then prnt->phijs->ppd and from the list chouse your printer. 
FINISH:)

Sory for mistakes:)

good luck:)

---

