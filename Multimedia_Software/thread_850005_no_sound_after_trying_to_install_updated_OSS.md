---
title: "no sound after trying to install updated OSS"
date: 2008-07-05
forum: Multimedia Software
---

### Post by briancb on 2008-07-05
I have been trying to get my mic to work. C-Media sound card. I tried to install the updated version of OSS oss-linux-4.0-1016_i386.deb. After trying to follow the instructions and failed miserably (the deb package would not work). I found the note where there was a patch but no idea how to run it. Now I have no sound at all.

My question is do I have to reinstall to get my sound back (it's fine when I run off the cd), or is there some other way?

---

### Post by LinuxRocks713 on 2008-07-05
> **briancb said:**
> I have been trying to get my mic to work. C-Media sound card. I tried to install the updated version of OSS oss-linux-4.0-1016_i386.deb. After trying to follow the instructions and failed miserably (the deb package would not work). I found the note where there was a patch but no idea how to run it. Now I have no sound at all.

My question is do I have to reinstall to get my sound back (it's fine when I run off the cd), or is there some other way?

What errors happen when you install the deb file?

---

### Post by briancb on 2008-07-05
Thank you for replying I gave up and reinstalled so I have my sound back now.  By the way it said could not open as the package may be corrupted or you are not allowed to open the file: please check permissions

---

### Post by LinuxRocks713 on 2008-07-06
> **briancb said:**
> you are not allowed to open the file: please check permissions

You could have solved it by:

sudo dpkg --install oss-linux-4.0-1016_i386.deb

,which runs it as root.

---

