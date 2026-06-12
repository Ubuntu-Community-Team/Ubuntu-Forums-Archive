---
title: "Accessing music on a NTFS drive in Ubuntu."
date: 2020-12-05
forum: Multimedia Software
---

### Post by kwjorders on 2020-12-05
Hello, I have installed clementine a music player on Ubunutu and have all my music  on a NTFS drive on my Windows 10 hard drive.  I used to have this setup in the past and could play all my music in Clementine this way but now when I try  to access the hard drive I have bookmarked in the files section it says  permission is denied.  I have the drive to auto mount on boot up but it  does not show up in the library folder scanner,

Thanks

---

### Post by crip720 on 2020-12-05
Did you use the snap to install clementine?  Snaps usually do not have permission to use other drives/partitions.  Can try to go back to softwarestore and give more permissions or install .deb package.

---

### Post by kwjorders on 2020-12-06
Thanks this worked.

---

### Post by CelticWarrior on 2020-12-06
It should be noted that the issue was snap permissions, not the file system.

---

