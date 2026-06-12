---
title: "[SOLVED] 2 hard drives and it showing low disk space?!"
date: 2008-09-23
forum: Mythbuntu
---

### Post by bmwman on 2008-09-23
Hello guys, I have a HTPC set up with 2 hard drives. First one is 500gb sata drive that has all my movies and music. The other one is 300gb IDE that has the Mythbuntu loaded on it(system partition) and the rest is free space - over 220GB. The 500gb drive is mounted under /home/backend/Media and everything is working fine. 

The problem is when I open the system information in mythbuntu it's showing that I have only 500gb and only 17gb free. It doesn't count the main drive which is being used for recordings and LiveTV.

Why is this happening and how to fix it?
Thanks

---

### Post by anonymousdog on 2008-09-23
It's only supposed to count space on file systems where there's a storage group defined.  So, if you changed the default storage group to point to /home/backend/Media, then, that's the only file system on which MythTV will calculate free space.  The point of the calculation is so MythTV can maintain free space on file systems it is configured to fill up (and leave the rest of the file systems alone).

---

### Post by bmwman on 2008-09-24
I think I set up a new storage group called Videos which is pointed to /home/backend/Media. The default group for recordings it's still under the default place and that's where it puts recordings. I'll take a look later after work to make sure.
Thanks for the hint.

---

### Post by nasha on 2008-09-24
Add the drive to the default storage group and you should have no problems

---

### Post by bmwman on 2008-09-24
I added my /var/lib/mythtv/recordings folder to the Default group and it shows in the system status now. I have added other folders in the Video storage groups but I assumed that the Default is already set since that's where it puts the recordings and Live TV anyway. I guess I was wrong.

Everything is good now. Thanks :)

---

