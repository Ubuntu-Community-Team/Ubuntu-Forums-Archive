---
title: "How can I check if my samba shares are being used"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by Captain_Glen on 2009-05-08
Hi,

I want to write a script that returns true if a samba share is in use.  So I can tell if a samba client is connected to my computer and have it block shutdown.

Any help would be appreciated.

---

### Post by mattgyver83 on 2009-05-08
If it is mounted to the drive you could cook something up from this point,

if [ $(mount | grep -c /mount/point) != 1 ]
#	tests if /mount/point folder is currently mounted
	then
             zenity --error --text="no drive mounted"
	
	else
		
fi

hope thats what you mean.

---

### Post by Captain_Glen on 2009-05-09
Thanks for the reply but I don't think that helps me.  I need the samba server to check if its samba shares are being used by an xbox client and if they are block the computer from shutting down.  The share folder is my external hdd and it is always mounted on the server.

---

### Post by Captain_Glen on 2009-05-12
I found an alternative.  I just wrote a script that returns true if it can ping the xbox.  Now it doesn't shutdown if the xbox is turned on.

---

### Post by Triptol on 2011-07-10
Just for the record: you can check smbstatus to see whether a share (or a file on that share) is being used.

---

