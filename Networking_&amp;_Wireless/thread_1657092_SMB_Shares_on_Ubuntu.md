---
title: "SMB Shares on Ubuntu"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by izzmit on 2010-12-31
Hello
I am trying to get my linux box to see shared files from my windows7 computer. In network view in ubuntu, i see the workgroup, and the 2 win7 PCs that are in it.

My wifes computer connects fine -- I doubleclick it and enter the username/password, and I can view the shared folders.

My computer (nearly identically configured) will not allow connection -- Each time I enter username/pass, it waits a moment and asks for login credentials again. 

I have tried disabling the 128bit requirement for shared folders, and also disabled the password requirement. Nothing ever works -- same "ask for password, wait, ask for password". 

This same thing happens on both a 9.10 and a 10.10 ubuntu computer. 
Thanks for any help.

---

### Post by PatchesTheCaveman on 2010-12-31
Do you have Windows Live Essentials installed on the Windows 7 computer?  The Windows Live Sign-In Assistant changes the way Windows communicates such that Samba cannot access its shares.  While the Samba developers have fixed this bug, Canonical has not released an updated package for Ubuntu with the fix.

To work around this problem, uninstall Windows Live Essentials.  Please note that Microsoft sometimes installs this software as part of Windows Update, so you may not be aware it is installed on your system.

---

### Post by izzmit on 2010-12-31
I just checked, and I do have Windows Live Essintals installed. When I checked what components were there, only Messenger showed up. So, I dont think that is it.

---

### Post by izzmit on 2011-01-02
Ok, I was wrong here.
The Windows Live Essentials pack only showed MSN messenger as being installed (Sign in assistant usually shows up here in this list or so I thought).
Add/remove programs didn't show any sign in assistant, even when viewing windows components.
When i went into windows services, I found that Sign On Assistant was indeed there and running. Uninstalling Live Essentials fixed the problem. Thank you very much for your help.

Solved!

---

