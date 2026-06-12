---
title: "Permanently mounting a Windows drive"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by Robin Nixon on 2009-10-16
Is there an easy way to permanently mount a Windows drive (or network backup drive)?

I use Places -> Connect to Server and enter the details and it works fine.

But after a reboot the drive is gone.

Under windows I can Map a drive to automatically mount each reboot. I can also easily do this on a Mac.

So is there an easy way to do this on Ubuntu without using the Terminal, sudo, fstab, cifs or anything like that? I mean is there a point and click solution with the mouse?

Thanks in advance for any help.

---

### Post by uncle-c on 2009-10-16
I'm afraid that you are going to have to edit your /etc/fstab file, but do not worry it is a very simple process. The very same question was asked yesterday ! :-)

[http://ubuntuforums.org/showthread.php?t=1291939](http://ubuntuforums.org/showthread.php?t=1291939)

---

### Post by Robin Nixon on 2009-10-16
Thanks uncle-c. I've made a brainstorm suggestion about this (awaiting approval at the moment):

[http://brainstorm.ubuntu.com/idea/21869/](http://brainstorm.ubuntu.com/idea/21869/)

---

