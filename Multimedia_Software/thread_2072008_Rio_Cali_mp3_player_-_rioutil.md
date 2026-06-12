---
title: "Rio Cali mp3 player - rioutil"
date: 2012-10-16
forum: Multimedia Software
---

### Post by webdesigncompanyla on 2012-10-16
I have a Rio Cali mp3 player and I have installed the command line drive but I am getting some errors.

I have Ubuntu 12.04.1 installed and rioutil_1.5.0-1_amd64.deb version of the driver.

This was working fine in a previous install of an older version of Ubuntu.

I have the same error in 10.04LTS, btw.

Here is the error I get:

$ sudo rioutil -i
Attempting to open Rio and retrieve song list.... failed!
Reason: No such file or directory.
librioutil tried to use method: libusb


Does anyone know how to get this working?

---

### Post by webdesigncompanyla on 2012-10-17
anyone?

---

### Post by webdesigncompanyla on 2012-10-26
bump

---

### Post by meffordm on 2012-12-09
I have the same problem.  Try using root.  That helped.  I still have to figure out my udev settings for it to work under a user.  BTW, I'm using Fedora, but it should be the same.

---

