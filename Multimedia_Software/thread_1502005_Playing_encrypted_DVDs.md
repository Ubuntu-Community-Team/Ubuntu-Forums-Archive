---
title: "Playing encrypted DVDs"
date: 2010-06-05
forum: Multimedia Software
---

### Post by zippyblue on 2010-06-05
After following instructions to install software to play encrypted DVDs, and after rebooting, I tried to play a DVD in Totem.  A driver was searched for by Totem; not found; DVD not played.

---

### Post by wojox on 2010-06-05
You used 

```
sudo apt-get install libdvdread4
```

From terminal:

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by sites on 2010-06-05
You can also go to [this site]("http://ubuntuguide.org") and look for the DVD playback section.

---

### Post by jerenept on 2010-06-05
Did you install libdvdcss? I think it is at 
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

After you install libdvdread4 or ubuntu-restricted-extras, just enter the above in a terminal.

---

### Post by zippyblue on 2010-06-05
I solved the issue using advice from another thread.



"I fixed it by entering these 2 scripts

Code:
sudo apt-get remove --purge ubuntu-restricted-extras
Code:
sudo apt-get install ubuntu-restricted-extrastook a hour or so on the Gigabyte desktop (seemed to uninstall all MS core fonts ?), but only took a minute on the Asus K52F notebook"

Thanks to Charonred



James

---

### Post by Gato Verde on 2010-06-09
I have done all of the above, including the comprehensive guide instructions, and still can't get a commercial DVD to play.

Any other ideas?

---

### Post by Brandel Valico on 2010-06-09
[http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback](http://ubuntuforums.org/showthread.php?t=766683&highlight=dvd+playback)

Have you tried these instructions?

---

