---
title: "Can't capture video with Kino."
date: 2010-03-01
forum: Multimedia Software
---

### Post by MSich on 2010-03-01
Ok, I can capture video from my video camera using Kino, but only if I launch the program as root.

sudo kino

If I do this, then it recognises my camera connected to my firewire card.  If I just launch Kino from the menu, it doesn't see the camera at all.

I have the version from the software center  installed (1.3.3).

Is there a way I can change the permissions so it can be launched by a normal user?

---

### Post by MSich on 2010-03-04
bump

---

### Post by realzippy on 2010-03-04
From
[https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire)  :

This method makes a new group called firewire  with control of the raw1394 device file, and your user a member of that group. The camcoder must be plugged in and turned on at boot time for this to work because udev will only create /dev/raw1394 if the camcoder is present and /dev/raw1394 must be created before bootmisc.sh is run.

   1.

      Open 'System > Administration > Users and Groups'. Add a new group and call it firewire
   2.

      Open the firewire group and add your user name to this group.
   3.

      Open a terminal and type

      sudo gedit /etc/init.d/bootmisc.sh

   4.

      At the end of the file type

      chgrp firewire /dev/raw1394

   5.

      Reboot, or to apply changes now type directly in a terminal

      sudo chgrp firewire /dev/raw1394

   6. Insure camcorder is connected and turned on before the system is booted.

---

### Post by MSich on 2010-03-04
Good link!  Thanks for the help.

---

### Post by nicefiddler on 2011-04-27
I am using Sony DCR-TRV460E which has a firewire port. I am using ubuntu 10.10 and have tried kdenlive as well as kino, but am unable to import dv through firewire. I am a noob. Please help.

---

### Post by damotor on 2011-05-08
sudo ln /dev/fw0 /dev/raw1394

---

### Post by nicefiddler on 2011-05-31
I tried this:
sudo ln /dev/fw0 /dev/raw1394
I got the message:
ln: accessing `/dev/fw0': No such file or directory

Issue remains unresolved. Please help. Is the problem caused because of the 64bit o/s?

---

