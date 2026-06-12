---
title: "Canon Pixma iP2702 printer on Ubuntu server cannot receive jobs from Windows XP/Vista"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by PlanoAlto on 2012-08-30
First, some background on the setup I am running:

My print server is a Dell Inspiron laptop (don't laugh) running Ubuntu 12.04 LTS, and it has a hard-wired connection to my wireless router. I installed the CUPS server and Samba onto it. The server accepts jobs without a hitch from my Windows 7 netbook and my Ubuntu 12.04 power desktop, but it cannot talk to either my Windows XP desktop or my Windows Vista desktop (upgrading either machine is not an option right now).

Here is the printers section from my smb.conf file:
```
[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = yes
   create mask = 0700
   use client driver = yes

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
   write list = root, @lpadmin

```The two computers which cannot connect to the printer react the same way. Both can see the printer fine, but they complain that the server does not have the correct driver installed and ask me to select the driver from a list. Both of them have the Windows driver I downloaded from the Canon website, but after choosing the driver I immediately get this message:
```
---------------------------
Connect to Printer
---------------------------
Windows cannot connect to the printer. Either the printer name was typed incorrectly, or the specified printer has lost its connection to the server.  For more information, click Help.
---------------------------
OK   Help   
---------------------------
```I am guessing there are some access permission shenanigans going on here. Could you confirm whether or not this is true or explain to me where the actual problem might lie?

---

### Post by dandnsmith on 2012-08-30
Have you followed up on the printer name?
Perhaps you should post it here, as there are some restrictions which are more notable for XP and Vista.

---

### Post by PlanoAlto on 2012-08-30
Pardon me because I'm not very familiar with Samba, but is that the CUPS name for the printer when you access [http://localhost:631/?](http://localhost:631/?)
Or is it that you need more information from my smb.conf file, and if so what data?

---

### Post by dandnsmith on 2012-08-30
I was referring to that message you posted:
[> ---------------------------
Connect to Printer
---------------------------
Windows cannot connect to the printer. Either the printer name was typed incorrectly, or the specified printer has lost its connection to the server.  For more information, click Help.
---------------------------
OK   Help   
---------------------------

So, what did you type?

---

### Post by PlanoAlto on 2012-09-03
Sorry I never quite understood your question, but I managed to solve the issue all by my lonesome.

Instead of going the Samba route, I used IPP on a freshly installed x64 copy of Ubuntu Server and all machines can now talk to the print server. Thanks for contributing your time to help me out!

---

### Post by dandnsmith on 2012-09-03
Glad you have a solution.
Intrigued to hear 'IPP', which a google search tells me is used in CUPS

---

