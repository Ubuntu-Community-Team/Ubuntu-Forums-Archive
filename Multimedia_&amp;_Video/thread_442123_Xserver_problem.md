---
title: "Xserver problem"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by abhishek456 on 2007-05-13
I am using Ubuntu 6.06

When i am browsing files with nautilus suddenly the icons of the files changed.
So i tried to restart the Xserver.But it failed. So i rebboted the system but i can't start Xserver.

I had an Via/s3 Unichrome graphic card. I changed it to Vesa in Xorg.conf but it din't work

I tried to reconfigure Xserver using > sudo dpkg-reconfigure xserver-xorg but it gave the fallowing error

> 

can't locate strict.pm in @INC (@ INC contains :/etc/perl/urs/local/lib/perl/5.7/usr/local.......................

at /usr/sbin/dpkg-reconfigure line 8

begin failed --compilation aborted at /usr/sbin/dpkg-reconfigure line8



i am attaching my both Xorg.0 log, Xorg.conf and /usr/sbin/dpkg-reconfigure files

---

### Post by abhishek456 on 2007-05-15
after placing strict.pm file in > /usr/lib/perl i got the next error > can't locate Debconf/Db.conf....................

compilation failed at line9(next line after which i got the above error).

I tried placing all .pm files mentioned in /usr/sbin/dpkg-reconfigure in usr/lib/perl but could not make sucess.I got the same error "can't locate Debconf/Db.conf"

so now in which directory must i place the files.

---

### Post by abhishek456 on 2007-05-16
any help from any one.............?

i am planning to reinstall ubuntu due to above problem!

---

