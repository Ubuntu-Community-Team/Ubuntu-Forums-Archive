---
title: "can't print to printer connected to comp with w7"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by mich4elp on 2010-12-29
We got a new computer with Windows 7 today as the main computer for our home network. However, I'm having troubles printing to the printer from my Ubuntu 10.10 computer.
I can see the printer, but when I try to add it, it asks for a password. There are no users on the Windows 7 computer with a password. All of the network sharing settings in Windows 7 are set to share printers and files without passwords.
Anyone know why it asks for a password?
Printer is Brother MFC-465CN.

---

### Post by PatchesTheCaveman on 2010-12-29
Do you have Windows Live Essentials installed on the Windows 7 computer?  The Windows Live Sign-In Assistant portion of that package changes the way Windows 7 utilizes the SMB protocol in a way that breaks the version of Samba included with Ubuntu.  While the Samba team has fixed the official version of their software, Canonical has yet to release an updated version for Ubuntu.

You can temporarily work around this problem by uninstalling the Windows Live Sign-In Assistant.  Please note that Microsoft sometimes installs Windows Live Essentials via Windows Update without the user's knowledge, so you may not be aware you have this software.

---

### Post by mich4elp on 2010-12-29
Nope, uninstalled Windows Live Essentials and still asks for a password. It stills shows up in the list of installed programs, but all components are removed.

edit: Wait, must of screwed something up. I'm uninstalling it now.

edit2: Okay, removing Windows Live Essentials solved the problem. Thanks so much!

---

