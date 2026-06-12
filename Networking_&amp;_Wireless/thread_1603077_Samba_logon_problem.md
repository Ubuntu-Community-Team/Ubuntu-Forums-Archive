---
title: "Samba logon problem"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by CatWeazel67 on 2010-10-22
Hi,

I have just upgraded to Samba 3.4.7 on Ubuntu 10.04 runing as a PDC

We have a short cut on the desktop which pointed to the server ( \\server ) Previously when we clicked this it asked for logon credentials immediatley.

Since the upgrade it shows a list of shares ( printers, netlogon etc ) and dosn't ask for credentials until you try to access a share.

This means the first time you click the server shortcut you wont see your home drive listed. You need to click one of the shares , logon then close the window and click on the shortcut again before you see your home drive.

I have gone through the smb.conf and turned off guest access on all the shares and anywhere else I could find it ( printer section etc ) .

How do I revert to the previous behavour ?

Many thanks

-- 
Simon

---

