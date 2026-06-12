---
title: "Umount problems"
date: 2010-09-20
forum: Networking &amp; Wireless
---

### Post by nathanbrett on 2010-09-20
Hi,

I am running into the problem of not being able to unmount a networked volume.  The volume was obtained through the ncpmount utility.

If I right click on the desktop icon and click Unmount, the system complains that it is not in the fstab(and you are not root).   

If I run the command line from a terminal "sudo umount novelclient", it unmounts the volume fine.  


I am interested in making a script that user's can click on to unmount this volume, instead of opening a terminal and using the command line.

If this is possible, or anyone knows of a better solution, please let me know :)   Thanks

Nathan

---

### Post by nathanbrett on 2010-09-22
I guess no one had any ideas :S :)

Anyways I was busy looking around the net, and came up with this solution:

Created a newfile called unmount.sh
Inside the file I added the following 2 lines.   

#!/bin/sh
echo yourepassword | sudo -S umount /home/user/novelclient        


Granted all permissions to all on file.  Created a launcher on the desktop which links to the script file.   Now click on the desktop to unmount the volume with no complaints :)

**Not a secure way obviously to fix the problem... you're password is easily findable :)  But in our case it doesn't matter... many users know the password :)

---

