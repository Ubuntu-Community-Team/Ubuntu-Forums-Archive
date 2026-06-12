---
title: "noob can access but not copy on network"
date: 2009-07-06
forum: Networking &amp; Wireless
---

### Post by sgian on 2009-07-06
Hello, I've just installed ubuntu on my kids' computer.  I've gone through the instructions on the following page [https://help.ubuntu.com/9.04/internet/C/networking-shares.html](https://help.ubuntu.com/9.04/internet/C/networking-shares.html) on how to put my ubuntu on my network.  I've got 2 computers with windows xp.  I have already unclicked the read-only box, and followed all the instructions on the page I linked to except nautilus, which I couldn't find.

-I can see the ubuntu computer from the windows machine, and open folders and files
-I can copy from the ubuntu computer onto windows, but can not copy files from windows onto the ubuntu computer
-I can not see the windows computers from the ubuntu computer when I open the network.
-attempting to open windows workgroup comes back with an error message about not being able to mount the share or something like that.

So what do I still need to do so that I can copy files and folders from the windows computers onto the ubuntu computer through the network? 

Thank you.

---

### Post by sgian on 2009-07-06
I just installed a dual boot ubuntu on a newer computer, and the newer computer networks just fine with the other ms computer.  Maybe the first ubuntu install was on a computer too obsolete for networking properly?

---

### Post by jumbofishmeat on 2009-07-06
Did you try looking in "Windows Networks" on the ubuntu computer, or did that not show up?

---

### Post by sgian on 2009-07-06
Selecting Windows Network results in an error message something like "unable to mount location"

---

### Post by superprash2003 on 2009-07-07
that is a bug. you should try accessing the folders this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by sgian on 2009-07-07
> **superprash2003 said:**
> that is a bug. you should try accessing the folders this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)
Thank you.  I was able to access one of the other computers by using the smb command, but not with nautilus.  So it must be a bug, but at least now I have a way of transferring files.

---

