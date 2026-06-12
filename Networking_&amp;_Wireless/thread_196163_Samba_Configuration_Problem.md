---
title: "Samba Configuration Problem"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by Sonofmoog on 2006-06-13
What I'm looking for is bi-directional read-write access via Samba between my Ubuntu 6.06 PC, and the two others on my home network running Windows XP and PC Linux OS.  

Both of the other systems can see the Ubuntu shares, but not access them.  I use two of the three machines as backups for the third, and since it's just me, I really need bi-directional read-write access without prompting for a password.  

In the KDE Control Center, if I enable advanced sharing in the Network-->File Sharing Panel, and set Security = Share in the Network-->Samba panel, this gets me what I need.  

But, how do I do this in Gnome?  :?:  I've looked for every network(ing) dialog I could find, and even tried hand-editing my smb.conf without success.  

All suggestions greatly appreciated.

TIA ..

---

### Post by DarthMandeep on 2006-06-13
I do this by editing my /etc/fstab file to supply the username and password when I mount the Samba share.

The entry looks something like this:

//servername/sharedfolder   /mountdirectory   smbfs username=yourname,password=yourpassword,users,noauto 0 0

You could change the "noauto" option to "auto" if you want the share mounted automatically at startup.

By the way, if you are using the Firestarter firewall, you will need to go to Edit --> Preferences --> Firewall --> Advanced Options and uncheck the "Block broadcasts from externel networks" option.

Edit - For some reason the "noauto" part of my example has a space in it even though it's typed as one word, so ignore the space.

---

### Post by Sonofmoog on 2006-06-14
Thanks for the reply, but that isn't my problem.  I'm not trying to mount any shares, either in Ubuntu or on the other machines.  When I open My Network Places in XP, the share names appear, but when I click on them, access is denied.  When I do so in PCLOS, a dialog pops up asking for a password.  I could probably solve this by adding a username and password to /etc/samba/smbpasswd, but I don't want to do that.  

I have bi-directional read-write access without confirmation from the other OSes on the Ubuntu machine (Windows XP and PCLOS), so I know there is nothing wrong with my hardware.  Smb is running as a system service, the server software is installed, and the shares are visible from the other PC's on the network.  But, they are not *accessible*.  So I have to believe my problem is smb.conf, or some other file like maybe /etc/hosts.allow.  I don't know enough about what the settings in those files should be to manually edit them.

---

