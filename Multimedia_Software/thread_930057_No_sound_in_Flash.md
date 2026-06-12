---
title: "No sound in Flash"
date: 2008-09-25
forum: Multimedia Software
---

### Post by Cclips on 2008-09-25
Rather new installation, I have sound in Amarok and everything else, but I don't have any from flash or youtube. I've tried reinstalling flash player, and the commands

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

&


```
chown -R <username>:users /home/<username>/.macromedia

```

To no avail.

Ideas?

---

### Post by gandaran on 2008-09-25
there are many fixes for the flash sound problem around
the first one is to install libflashsupport for flash 9
the second and recommended is flash 10, the new flash 10 release and the firefox 3.0.2 work very nice
if these two don't work for you, there are other fixes, just search the forum
if you haven't tried any of these fixes, you should undo those commands or anything you have done so far.

---

### Post by Cclips on 2008-09-25
The libflashsupport fixed it, thanks. 

As a note, FF3.0.3 apparently is out, but it didn't in itself fix the problem. 

How do I go about undoign those other fixes however...?

---

### Post by Bakon Jarser on 2008-09-25
> **Cclips said:**
> The libflashsupport fixed it, thanks. 

As a note, FF3.0.3 apparently is out, but it didn't in itself fix the problem. 

How do I go about undoign those other fixes however...?

That's because it's not a Firefox bug.  If your problem is fixed don't bother undoing the other changes.

---

