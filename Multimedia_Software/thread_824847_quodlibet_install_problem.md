---
title: "quodlibet install problem"
date: 2008-06-10
forum: Multimedia Software
---

### Post by itzig on 2008-06-10
hello, I am running hardy, and recently had to uninstall quodlibet. I did that with the package manager, and then deleted the folders: home/user/.quodlibet
usr/share/quodlibet

But now when I try to reinstall something goes wrong.
$ quodlibet
Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 19, in <module>
    import config
ImportError: No module named config

I went to check those directories, and there are only a three files in 'usr/share/quodlibet, and there is no directory at all in the 'home/user/ directory!

Can anyone tell me how to fix this?

thanks!

---

### Post by itzig on 2008-06-13
There is nothing that can be done?

---

### Post by lolobu on 2008-06-14
So you don't have a config.py under /usr/share/quodlibet is that right ?
It seems to me that since you deleted manually /usr/share/quodlibet (bad idea), Synaptic believes that you still have it and therefore, doesn't reinstall this part.
You could try from Synaptic "select for complete removal" (not sure about the exact term, I don't have an english version of ubuntu) and then, reinstall quolibet again.

---

### Post by itzig on 2008-06-16
that's what I thought, but it didn't work!
however, I just grabbed all those files from another box, and put them in that directory, it did the trick!~

thank you!

---

