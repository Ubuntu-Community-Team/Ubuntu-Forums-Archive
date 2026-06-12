---
title: "Replace Media Drive Mythbuntu"
date: 2010-11-03
forum: Mythbuntu
---

### Post by turbodude on 2010-11-03
Hi guys, I have a Mythbuntu combined backend/frontend that has one drive for the OS and 2 other drives for recordings. One of the recordings drives was an old 500GB drive that didn't work in WindowsXP but seemed to be fine in Mythbuntu when I first installed it. Recently I have been getting a message saying the it needs to check drive for errors etc etc. I can press C to bypass the check and it generally starts OK. Anyway I want to remove the failing recordings drive. I am not terribly worried about saving the recordings that are on it. 
 
What is involved in cleanly removing the drive so I can continue to use MythTV with the recordings that are on the 3rd good drive? Please keep in mind I am pretty new to Linux but happy to learn.

---

### Post by jayman8547 on 2010-11-03
It depends on how they are mounted...do a df -h and it will tell you what folder is mounted to what drive.

I just replaced a 500gb storage drive and a 1tb mdadm raid array with 2 new 2tb drives.  All i did was load the drives up in an external usb sata dock, mounted temp folders and copied over all the data.  Then in the backend I replaced the drives in question and remounted them in fstab.  If none of that makes sense let me know and I can explain in more detail.

---

### Post by LowSky on 2010-11-03
Ubuntu will check a drive every 30 or so computer boots.
There is more than likely nothing wrong with the hard disk.

---

