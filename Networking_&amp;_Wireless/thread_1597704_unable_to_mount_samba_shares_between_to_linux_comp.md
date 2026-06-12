---
title: "unable to mount samba shares between to linux computers"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by poboy975 on 2010-10-15
hi, i've been searching for a solution to my problem for a couple of days now. i have a ubuntu 10.10 desktop and laptop. i installed samba, and smbfs. i shared a folder on each computer. when i browse the network i can see the laptop from the laptop, and can see the desktop from the laptop, but i cant see the laptop from the desktop. when i try to mount the share it says unable to mount, but mounts it anyway...but, i need to be able to mount it so that rsync will see the shares as a dir on the desktop. i tried manually mounting via smbmount following several threads that i found, and i keep getting error sudo smbmount //192.168.1.78/share /media/laptop
Password: 
Unable to find suitable address

that is as far as i've been able to get. i've looked and have only been able to find threads about windows shares, not between 2 ubuntu machines. and i dont know why laptop can see the desktop but not the other way around. they have identical smb.conf files

---

### Post by CMOS4081 on 2010-10-15
Try using Places from the top menu bar then connect to server and manually input the name of the system. Make sure both systems have different names.
Try using the option to share folders from the file manager itself, nautilus.
Share the folder with with guest access, just to check if you can see the folder.
also you could try adding the shared folders by using the mount command and specifying its a samba mount.

Or do it the right way by using NFS instead of Samba (since you are sharing between two Linux boxes instead of with Windows) From other peoples comments in other forums, transfer rate of files is also faster. (I guess because it is the native server/client network file system in Unix).

good luck!

---

### Post by pricetech on 2010-10-15
Or SCP.  Just install openssh-server on both and use Connect to Server choosing SSH as the Service Type.

---

