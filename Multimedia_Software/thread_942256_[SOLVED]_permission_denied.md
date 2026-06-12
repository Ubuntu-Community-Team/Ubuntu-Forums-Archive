---
title: "[SOLVED] permission denied"
date: 2008-10-09
forum: Multimedia Software
---

### Post by fishbulb1022 on 2008-10-09
I'm trying to create a channels.conf file using w_scan. When I try to run it, it says permission denied, even when done as root. I found the actual file itself on my computer to try and change the properties, thinking it may have been a read only file, but it said since i did not own the file and could not edit the permissions. Does anyway know of a way to change this? thanks

---

### Post by kabotage on 2008-10-09
type
```
sudo nautilus
```and it will grant root priviliges to nautilus, open up in /root with full access to all files/folders

*Take note that running programs with root privileges can be potentially dangerous as there is no protection for the user. Take due care and always understand what you are doing before messing with important files and remember to back up!*

---

### Post by Yellow Pasque on 2008-10-09
nautilus is a graphical program, so use gksudo, not sudo.

---

### Post by fishbulb1022 on 2008-10-12
Thanks for the help, worked great

---

