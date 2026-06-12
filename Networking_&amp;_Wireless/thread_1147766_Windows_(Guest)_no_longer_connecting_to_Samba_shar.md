---
title: "Windows (Guest) no longer connecting to Samba share"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by donovanh on 2009-05-03
Hi,

I'm running jaunty as host, and recently set up samba and managed to have windows in virtualbox connect to a second harddrive. When I switched on my computer today, the windows install can no longer find the shared drive, either through samba or the vboxsvr share.

What can I do to find out the issue?

Don

Edit: I think it's solved. I had installed Storage Device Manager (pysdm) in order to set up fstab and have the drive mount automatically. I had set the user to root and the drive to read only. Changing the settings to "defaults", and updating the folder's name in samba's conf file, has made it accessible again.

---

### Post by donovanh on 2009-05-03
^^ [solved]

---

