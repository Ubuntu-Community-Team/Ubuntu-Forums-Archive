---
title: "Applications in Kubuntu can't see network"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by maf1 on 2009-01-24
Hello,

I'm running Intrepid and have SMB setup with a username & password which allows me to access a windows network via dolphin. However none of the other applications can see it. For example the "build collection" button in AMAROK shows all of the local files but not the network. 

Any ideas very much appreciated

---

### Post by dukeinlondon on 2009-01-24
I think the issue is that Dolphin navigates and mounts network drive "on the fly". You need to permanently mount the network drive by adding an entry into /etc/fstab along the lines of 

//mediacenter001/backup /home/mediacenter cifs guest,noperm,dir_mode=0777,uid=uruser,gid=users,auto ,rw 0 0

Look for more information on how exactly to do it but that's the way to go I think

---

### Post by AlanR8 on 2009-01-24
I use a program called smb4k that has a nice graphical interface and will show all machines and shares on your network, including Windows and Mac. All you have to do is double click the share to mount it. There are options to automatically remount on reboot.

Nice bit of software.

> sudo apt-get install smb4k

---

### Post by maf1 on 2009-01-25
Thanks guys. I'm using smbk4 which works well. Once I have confidence I will try and edit /etc/fstab for permenant fix.

---

