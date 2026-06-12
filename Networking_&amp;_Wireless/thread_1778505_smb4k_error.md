---
title: "smb4k error"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by CeeCeez on 2011-06-09
Installed smb4k on a fresh install of 11.04.  When I tried to save the changes after setting up the preferences in smb4k, I got this error message:

Configuration file "/root/.kde/share/config/smb4k_sudowriterrc" not writable.
Please contact your system administrator. 

The file does not exist.  There is only one file in the directory: kdebugrc

I have smb4k successfully running on an EEE 1201PN with 11.04.  Seems crazy but when I check this machine, there is no directory in root .kde.  Can someone please help or suggest where to start?  We need smb4k as all data is stored on a server.

---

### Post by Zorael on 2011-06-09
Are you trying to start it as root? Shouldn't that be unnecessary if you set up the Super User configuration tab?

---

### Post by CeeCeez on 2011-06-09
I am not trying to use smb4k as root.  Unless something happened during the install that I am not aware of. It was when I configured the program, went to "super user" and ticked both boxes, clicked apply and that's when I got the error message.

Now when I try to mount a share it gives me the message:  Unable to find suitable address.


I have used smb4k over many years and had many problems with it but nothing like this.

---

