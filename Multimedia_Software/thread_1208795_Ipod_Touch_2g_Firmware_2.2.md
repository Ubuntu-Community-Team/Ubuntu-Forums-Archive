---
title: "Ipod Touch 2g Firmware 2.2"
date: 2009-07-09
forum: Multimedia Software
---

### Post by CaseSensative on 2009-07-09
Hello. Is there any good software to add or remove music to my Ipod? I previously tried jail breaking my ipod but the tar.bz2 file would not open. Any help would be appreciated.

---

### Post by wojox on 2009-07-09
Try this:

```
tar jxvf <filename.tar.bz2>
```

After that look in the directory it made for a file telling how to install.
Usually ./configure, sudo make install

---

### Post by CaseSensative on 2009-07-09
zinn@zinn-desktop:~$ tar jxvf redsnow-linux_0.3.tar.bz2
tar: redsnow-linux_0.3.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
zinn@zinn-desktop:~$ 


I have the file downloaded and I extracted it.

---

### Post by wojox on 2009-07-09
Delete and download it again something may have broke when opening previously.

```
tar xjvf redsnow-linux_0.3.tar.bz2
```

And make sure your in the same directory as the file when you unpack it.

---

