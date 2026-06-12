---
title: "VPN settings won't save?"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by Ferrat on 2009-09-09
Well, 
as the topic says, for some reason I can't save my VPN settings 

The Apply button as you can see is greyed out and no matter what I put in to the settings that doesn't change? 

I'm using OpenVPN, is there something I'm missing? looked around and looks like VPN on Ubuntu is a hassle, specially through Network Manager?

---

### Post by dave37 on 2011-03-01
exact same problem here with  netbook edition

---

### Post by stephsphynx on 2011-08-23
In case anyone is still interested, I was unable to apply changes to an existing VPN or set up a new VPN, both due to the "apply" button being greyed out.  Turns our I had migrated all my stuff to a new user account on the same machine and that had broken the VPNs but none of the other NM options.

My solution:
1. In Network Manager, export the existing VPN config via the "export" button.
2. Look at that file (Gedit will do) and check the paths to the keys, they should be in "/home/yourname/.VPN-keys-yourname".
3. Edit paths where needed.
4. Verify that you have permission to use those files, if in doubt use "chown -R yourname:yourname /home/yourname/.VPN-keys-yourname".
5. Delete the old VPN confin in NM.
6. Import your new and improved file.

Good luck!

---

### Post by joalin on 2011-11-14
i have the same problem. The save button is greyed out. Unfortunately I have no existing vpn to export. In my other pc i have, but I receive an error when trying to export it, and I cant find any in the file system either :-(

---

