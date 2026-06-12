---
title: "Problems with Blackberry 8100 Pearl"
date: 2008-10-27
forum: Multimedia Software
---

### Post by hackarre on 2008-10-27
Hello to everyone,

I've was recently given a Blackberry,and I want to add all my evolution stuff on it.

I've installed all barry software of this page [http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564](http://sourceforge.net/project/showfiles.php?group_id=153722&package_id=170564) 

I've first could charge my blackberry, but when I actually runned barrybackup, my phone couldn't be found. Then I decided to reinstall all this software, and now it's not even charging!

I guess that some dependency is needed, but I have no idea about it. 

Ubuntu is detecting it:


hackarre@hackarre-desktop:~$ lsusb
Bus 006 Device 031: ID 0930:0b03 Toshiba Corp.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:0b0c Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 016: ID 0fca:0004 Research In Motion, Ltd.
Bus 001 Device 014: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 001 Device 013: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000 



But I can't detect it with barry's software, and no it's not charging. It appears on screen: "No Blackberry found".


I would appreciate any help.

Thanks in advance.

---

### Post by bobbycheetah on 2008-12-01
I've finally revisited trying to figure out how to get my BB 8100 Pearl to be seen as a storage device so that I can transfer pic from my phone to my linux box (ubuntu 8.04).  try this:  sudo bcharge -o

I was then able to use the barrybackup tool successfully.  I just stumbled on this and it worked to get my phone to be recognized by the utility and perform a backup.  Now, I've just got to find how to see it as a storage device - without having to have a micro SD card...

---

