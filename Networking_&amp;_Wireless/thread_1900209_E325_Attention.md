---
title: "E325: Attention"
date: 2011-12-25
forum: Networking &amp; Wireless
---

### Post by silly35 on 2011-12-25
I am trying to edit my IP settings to change my IP settings from Static back to dhcp but when i try and save my sudo vi edit i get the following error. 
 
Please help!

 
E325: ATTENTION
Found a swap file by the name "/var/tmp/interfaces.swp"
          owned by: root   dated: Sun Dec 25 17:50:38 2011
         file name: /etc/ethernet/interfaces
          modified: YES
         user name: root   host name: FileServer
        process ID: 2555
While opening file "/etc/ethernet/interfaces"
(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.
(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/ethernet/interfaces"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/var/tmp/interfaces.swp"
    to avoid this message.
Swap file "/var/tmp/interfaces.swp" already exists!
[O]pen Read-Only, (E)dit anyway, (R)ecover, (D)elete it, (Q)uit, (A)bort:

---

### Post by drdos2006 on 2011-12-25
Press (D) to delete the swap file, then re-edit 

regards

---

