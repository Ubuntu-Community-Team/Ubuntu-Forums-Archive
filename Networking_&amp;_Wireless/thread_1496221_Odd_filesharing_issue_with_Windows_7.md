---
title: "Odd filesharing issue with Windows 7"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by dafreak on 2010-05-29
Well folks I'm not quite sure what has gone wrong but for some peculiar reason I can no longer connect to my Windows 7 machine on the network. I used to be able to connect to it and read files from it just fine. Now Ubuntu just repeatedly asks for the username & password and never connects to the system. I'm able to connect to a Windows 2000 Server that I have on the same network so SAMBA in that respect seems to be working just fine. This is with Ubuntu 10.04. The Windows 2000 Server can also see and access files on the Windows 7 machine just fine. I'm not sure if the problem is with the Windows 7 machine or something with the Linux machine. If there are any logfiles that I need to post lmk.

---

### Post by dafreak on 2010-06-02
Anyone at all? I'm willing to post more information I'm just not seeing anything in my log directory that indicates what the error is that is occuring.

---

### Post by dafreak on 2010-06-03
Found the solution here: [http://ubuntuforums.org/showthread.php?t=1473285](http://ubuntuforums.org/showthread.php?t=1473285) . There's quite possibly a lot of folks that are having this issue and don't know that the Windows Live Sign-In Assistant is the cause of the issues. I believe it was installed as part of an automatic Windows Update.

---

