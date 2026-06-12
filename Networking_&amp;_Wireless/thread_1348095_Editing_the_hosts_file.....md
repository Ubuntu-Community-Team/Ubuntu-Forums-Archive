---
title: "Editing the hosts file?...."
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by VcDeveloper on 2009-12-06
Is there a Software Module I can use the edit the host file?

---

### Post by Iowan on 2009-12-06
I ordinarily just use **nano**.

---

### Post by VcDeveloper on 2009-12-06
I need a su editor/file manager/terminal in order to modify the host file.  I can't seem to find one in Xubuntu?  How can I create a menu with a su app?

---

### Post by Iowan on 2009-12-07
I'm not as familiar with Xubuntu (power supply died on my Xubuntu machine before I got much use out of it). Ordinarily, you should be able to use **sudo** (ie. **sudo nano /etc/hosts**. (I may have messed up the path...)

---

### Post by VcDeveloper on 2010-01-13
Thanks for your help!  I appreciate it very much!

---

### Post by SuperSonic4 on 2010-01-13
Isn't mousepad xubuntu's default editor? In which case: ```
gksu mousepad /etc/hosts
```


Although I just use sudo nano

---

