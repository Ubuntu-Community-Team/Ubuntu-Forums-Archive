---
title: "Can't connect to Windows 7 PC for Shares or Printers"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by wiseguy12851 on 2010-12-31
I have a Windows 7 PC that I use and am trying to connect to for the printer and for files that are being shared. It finds it in Network connections but when the Authorization dialog pops up it always fails to authorize even though I know I'm entering the information correctly.

---

### Post by PatchesTheCaveman on 2010-12-31
Do you have Windows Live Essentials installed on the Windows machine?  The Windows Live Sign-In Assistant changes the way Windows communicates via the SMB protocol just enough to break the version of Samba included with Ubuntu.  The Samba developers have fixed the bug but Canonical has not released a package with the new version to Ubuntu users.

To work around this issue, uninstall Windows Live Essentials from the Windows computer.  Please note that Microsoft sometimes installs this software via Windows Update so you might not be aware it's on your system.

---

### Post by wiseguy12851 on 2011-01-01
Sorry for the late reply, That did fix it. I only had 1 component of Live Essentials installed and after removing it everything worked.

---

