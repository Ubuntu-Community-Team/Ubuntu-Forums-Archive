---
title: "Error Messages while trying to install ubuntu - restricted access"
date: 2007-08-28
forum: Multimedia &amp; Video
---

### Post by f00d4tehg0dz on 2007-08-28
so i did sudo apt-get install ubuntu-restricted-extras to get all the codecs that the guide tells me.. BUt then my laptop froze.. and now i went to redo it, and i got this
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


so i did dpkg --configure -a and got nothing.. i don't know what to enter there or what.. and then redid sudo apt-get install ubuntu-restricted-extras and i got  the same messages to unpack etc.. but then got a java screen looking liek this,(found in attachment) with no way to get around it, please help me so i can get working codecs :)

---

### Post by f00d4tehg0dz on 2007-08-28
i think i got it

i read another post, from someone havine a dpkg problem. and never noticed U NEed to aDD SUDO to the beginning of the command.. and now everything seems to be working :)

sorry for the trouble

---

### Post by bapoumba on 2007-08-28
Glad to see you sorted this out on your own :)
Here is the long answer:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

