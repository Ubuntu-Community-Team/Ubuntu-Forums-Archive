---
title: "windows share no longer mounting"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by wgato on 2009-02-11
i noticed earlier today that i could not get to some files in my windows share any longer.  i couldnt figure out why and rebooted the machine and ran the same mount command i always do
~$ sudo mount -t cifs //192.168.1.27/"music drive"/ /mnt/music/ -o username=wgato,password=mypassword
mount error 110 = Connection timed out

using the File Browser i can navigate to directory.

checking the windows machine the directory is still shared.


any one have any ideas?

---

