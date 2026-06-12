---
title: "Cannot Mount External Hardrive... not anymore anyway"
date: 2010-07-04
forum: Networking &amp; Wireless
---

### Post by noworldorder on 2010-07-04
Ubuntu 10.4

 made a script to mount an external hard drive that is connected to my  router (Media Vault 2020)

this is the script:

#!/bin/sh
mount -t smbfs //192.168.1.104/MediaShare /mnt/MediaShare 
mount -t smbfs //192.168.1.104/Backup /mnt/Backup
Ubuntu 10.4

Well the script was working fine and then...  it stopped working upon  bootup.  But I could run the script in terminal after bootup and the  hard drive would mount fine.

Now, for no apparent reason, I cannot communicate with the external hard  drive at all.

 	Quote:
 	 	 		 			 				chris@chris-laptop:~$ gksudo  /home/chris/Documents/SCRIPTS/automount.sh
mount error(113): No route to host
Refer to the mount.cifs(:cool: manual page (e.g. man  mount.cifs)
mount error(113): No route to host
Refer to the mount.cifs(:cool: manual page (e.g. man  mount.cifs)
chris@chris-laptop:~$  			 		 	 	 
So I am 100% noob and would appreciate any and all help.

Thanks - chris

---

### Post by khuttger on 2010-07-04
Be sure the drive is at the same internal IP, they change sometimes so look into that.

---

### Post by noworldorder on 2010-07-04
you were right! The IP changed thanks

---

### Post by khuttger on 2010-07-04
Glad I could help, I remember I had a problem like this with a printer.

---

