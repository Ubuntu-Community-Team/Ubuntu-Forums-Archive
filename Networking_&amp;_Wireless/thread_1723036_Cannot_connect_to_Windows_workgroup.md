---
title: "Cannot connect to Windows workgroup"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by MadMatter on 2011-04-06
Ok long story short. I need to reinstall the samba directory, mainly to get the default smb.conf. It appears I have to remove smbclient, which takes ubuntu-desktop with it (which I now know is mostly ok). Hopefully reinstalling those will then replace /etc/samba. There's enough troubleshooting samba threads out there for the rest. I'll flag this solved when I'm done.

I am working on setting up BackupPC on Maverick , for my network. I am unable to view my WinXP machine's shares if I type "sudo smbclient -L //JonDoe/" . However it works if I use the XP machine's IP "sudo smbclient -L //192.168.1.100/". Viewing the workgroup (with the proper name) in Nautilus only shows the Ubuntu machine. I ended up using multiple how-tos which had me install the following packages : Samba, smbfs, system-config-samba. With all that nothing worked so I decided to uninstall the above with "remove completely" in synaptic, expecting everything to be completely gone. But /etc/samba with smb.conf still existed so I deleted it. :-o OOPS!!! :-o. Installing Samba after the uninstall did not create a new /etc/samba/ directory. Reinstalling smbclient in synaptic didn't create it either. Uninstalling smbclient with pull BackupPC with it. Sweet! I do have a firewall package installed which allows outgoing but blocks inbound traffic from outside my LAN. I will disable it when I get home. Any solutions would be much appreciated! Thanks.

---

### Post by MadMatter on 2011-04-10
Finially got samba to work. Samba-common might be responsible for the samba directory. Winbind package is required for netbios name resolution to occur, it is not a default package. Other steps were required [http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
. Now I've decided to attempt Bacula instead.

---

