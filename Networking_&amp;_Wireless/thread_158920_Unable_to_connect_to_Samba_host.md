---
title: "Unable to connect to Samba host"
date: 2006-04-11
forum: Networking &amp; Wireless
---

### Post by neoaddict on 2006-04-11
I'm trying to print to a Windows printer from Ubuntu, but I keep on getting an Unable to Connect to Samba Host in the status of the printer's properties windows.

The printer keeps on printing blank pages.

Any ideas?  :confused:

---

### Post by neoaddict on 2006-04-15
Bump.

---

### Post by daWabbit on 2006-04-17
Make sure that sharing is enabled on the Windows box. It wouldn't hurt to delete the printer, then redo it with sharing enabled. I had to do that here. 

Then, when adding the printer in the system admin tools on Ubuntu, make sure the printer is listed so the correct driver gets installed. If it is not, it may not be supported. A few are not listed there, but support can be added, so don't give up hope if you don't find it in the list. 

That is all it has taken here. I can access printers hooked to Ubuntu machines from both other Ubuntu boxes and Windows boxes. I can also print on three specialty printers hooked to Windows machines, including an envelope printer and an old HP Plotter. 

Jack

---

### Post by neoaddict on 2006-04-21
It sort of "prints" - nothing appears on the sheet that comes out of the printer.

---

### Post by neoaddict on 2006-04-23
Do you know what I put for Host, Printer, Username and Password in the Windows Printer [SMB] area?  I've tried various combinations, it either gives me nothing, or a blank page.

Also, does the Lexmark 5000 PPD work for Lexmark 5200's?

---

### Post by neoaddict on 2006-04-26
Bump.

---

### Post by Iowan on 2006-04-27
Just a blind guess (but also serves as a bump...), the host and printer would be the Windows machine.  An even blinder guess would be that the username and password would be one for the Windows box.  
  Is Samba involved in this process (the **Windows Printer [SMB] area** has me curious.)?

---

### Post by neoaddict on 2006-04-29
I've tried doing that, no luck.  At best it gives me a blank page with nothing on it.

---

### Post by ryan on 2006-04-29
I am not sure about your setup but I print from an Ubuntu box to a shared printer on a Windows Domain. In the printer connection properties under "Printer type' I have "Network printer" checked and them I am using CUPS. I just punch in the printer's IP in the URI box and it seems to work fine.

---

### Post by neoaddict on 2006-05-01
How do you figure out your printer's IP?

---

