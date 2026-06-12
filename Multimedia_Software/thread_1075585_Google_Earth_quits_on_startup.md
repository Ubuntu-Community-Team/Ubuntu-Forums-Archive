---
title: "Google Earth quits on startup?"
date: 2009-02-20
forum: Multimedia Software
---

### Post by theunixgeek on 2009-02-20
I followed all the community instructions for installing Google Earth, installed it and reinstalled it independently various times, but every time Google Earth 5 loads up its screen shows for a second or two, then quits. What should I do to fix this?

---

### Post by binbash on 2009-02-20
go the the google earth folder and rename this file anything you want : 

libcrypto.so.0.9.8

Example : 

mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.backup

---

### Post by theunixgeek on 2009-02-20
> **binbash said:**
> go the the google earth folder and rename this file anything you want : 

libcrypto.so.0.9.8

Example : 

mv libcrypto.so.0.9.8 libcrypto.so.0.9.8.backup


that works, thanks a bunch :D

---

### Post by BDNiner on 2009-02-20
Work perfectly for me also. Thanks a lot.

---

### Post by scrat the elder on 2009-02-23
Oh the joys of a quick fix thank you :D

---

### Post by wirewrangler on 2009-02-24
I changed that file, and now that google earth opens, I get odd artifacts and psychedelic static. 

here is a short portion of lspci:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

### Post by clemm on 2009-02-25
I dont wish to sound stupid but I have the same problem, and that hasnt worked for me. I changed google earth to google eart_h.
Im wondering wich folder I need to change I have several google earth folders. google earth icon to run program, google earth linux.bin, google earth linux . bin .tar gz

---

### Post by binbash on 2009-02-26
you are not going to rename the folder.Read this : 

[http://ubuntushell.blogspot.com/2009/02/howto-install-google-earth-50-beta-on.html](http://ubuntushell.blogspot.com/2009/02/howto-install-google-earth-50-beta-on.html)

---

