---
title: "Network Printer"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by Aarookie on 2009-02-08
Hi all,

I had my network printer working, I can't find the article that helped me get there.  I was trying to get it working on my laptop, and in reviewing the settings on my desktop I screwed something up.  I remember vaguely that the default printer setup in system/admin/printer was not working so... The article suggested installing gnome cups printer selection.  Then I think you had to install the printer on a local port, when that was completed you went to preferences and changed to smb printer.  But no matter how I try it, it's not working this time.  I've tried the localhost:613 from browser and it doesn't see the printer.  Then I found this tid bit of info to help in that situation, but a standard install of ubuntu doesn't even have half of this stuff in directories and I'm at my wit's end.

First verify that you have the file /opt/samba/bin/smbspool
Then go to the folder /usr/lib/cups/backend
Inside this folder you need to make a symlink to the smbspool file and name it "smb".
Open a console and type: ln -s /opt/samba/bin/smbspool smb

Restart CUPS with the command: /etc/init.d/cups restart (or reboot Puppy)
Open the CUPS web interface and start installing a new printer.
At the bottom of the Device list you should now see "Windows Printer via Samba"
Make the device URI smb://PC_NAME/PRINTER_NAME 

First I don't have the file /opt/samba/bin/smbspool, my opt folder is empty.  Second the smb symlink appears to be in the usr/lib/cups/backend directory, but it doesn't exactly tell me where it's linked too.  The /etc/init.d/cups doesn't do squat.  So how does an ubuntu user get the localhost:631 to recognize a samba printer.

---

