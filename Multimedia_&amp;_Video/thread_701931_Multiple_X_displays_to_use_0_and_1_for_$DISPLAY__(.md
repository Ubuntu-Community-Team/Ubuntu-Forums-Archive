---
title: "Multiple X displays to use :0 and :1 for $DISPLAY  (not multiple monitors)"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by earnoth on 2008-02-19
How do I configure ubuntu to start X with more than one display?  (not multiple monitors or split screens...I just want to be able to have both DISPLAY=:0.0 and DISPLAY=:0.1 for different programs, toggling with CTRL-ALT-F7 & CTRL-ALT-Fsomething_else

In the old days, I'd have found the script that started /usr/bin/X and edited the args by hand.  But, native Ubuntu uses GDM, so I'd like to find the 'correct' way to do it (so I can keep using native GDM and not break on future updates).  

Is there an easy way to do it, so that I see 
```
/usr/bin/X :0 :1 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt7
```
in ps instead of 
```
/usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt7
```

---

### Post by nick_h on 2008-02-20
Have a look in your */etc/gdm/gdm.conf* file.  It looks like it could be as easy as adding an extra line to the [servers] section.

---

### Post by nick_h on 2008-02-21
It would also be worth reading - [ How-to run Multiple (Virtual) X sessions](http://ubuntuforums.org/showthread.php?t=271674).

---

