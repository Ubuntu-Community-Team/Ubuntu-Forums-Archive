---
title: "cannot enable accelerated ATI graphics driver"
date: 2009-08-11
forum: Multimedia Software
---

### Post by shmish on 2009-08-11
I'm interested in enabling my accelerated ATI graphics driver, as explained near the beginning here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")  However, System - Admin - Hardware drivers doesn't list a video driver, so there is nothing to enable

I'm running 9.04, and I'm pretty sure there was a hardware driver listed here when I had 8.10

From the above link, I ran
```
sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
```

I then tried to run
```
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
``` 
but got an error:
```
insmod: can't read '/lib/modules/2.6.28-14-generic/volatile/fglrx.ko': No such file or directory
```

I have an ATI x700 card, as confirmed with lspci.  The reason that I would like to get the fglrx driver working is because I'm trying to run XBMC which I think requires openGL.

thanks

---

### Post by markbuntu on 2009-08-11
The propietary ati driver available for 9.04 does not support your card. You should be using the open source ati driver which does.

---

### Post by tgalati4 on 2009-08-11
If you need to use the proprietary driver than you need to downgrade to 8.10.  Tell us what is not working with the open source driver in 9.04.

---

### Post by shmish on 2009-08-12
thanks for the replies.
I'm trying to run XBMC (xbox media center).  When it starts, the splash box opens and then closes right away.  I'm pretty sure this is a video driver issue, I think I had it happen when I first installed 8.10.

I'll most likely go back to 8.10 I guess.

cheers

---

