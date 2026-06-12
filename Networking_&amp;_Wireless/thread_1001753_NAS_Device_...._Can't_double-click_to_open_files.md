---
title: "NAS Device .... Can't double-click to open files"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by KhipuX on 2008-12-04
I've got an Intel NAS device which appears on our network under Ubuntu as a Samba network although I can assure that it is a standalone device. Originally the network was running a group of Windows clients and we're just slowly migrating across to Ubuntu.

Accessing the device works fine and I have no trouble setting up new directories or placing files on it. However, in Ubuntu, if you double click on a file to open it the application on the client briefly opens up on the task bar and then closes again. No matter what file type it is we can't open the files directly from the device. Instead we have to copy the file and paste to Ubuntu's desktop and then open the file. When we've finished with it we have to cut and paste back.

Secondly, we can't move files from one directory to another using drag and drop. We have to cut and paste otherwise we get an error saying the file already exists - which it doesn't in the target directory.

Has anybody got any idea what is going on? This never happened with the XP machines and I can't find this anomaly anywhere else on the net.

---

### Post by Iowan on 2008-12-05
No guarantees, but try setting up a fstab mount - [http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

