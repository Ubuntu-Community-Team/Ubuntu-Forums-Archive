---
title: "&quot;Monitor Resolution Settings&quot; behaving strangely"
date: 2008-08-24
forum: Multimedia Software
---

### Post by thepipirate on 2008-08-24
Hello,

I am getting behavior I don't expect from the Monitor Resoultion Settings dialog.  It is similar to [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=887846](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=887846) but the solution posted there, I think, is specific to an ATI card; I am using an intel:

```

rbowen@fluffy:~$ lspci | grep -i graphics
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

```

on my HP Pavillion dv5000.

My problem is this: I can detect both the laptop monitor and second external monitor. They are located one on top of the other (and this is the behavior I get when using the setup).  So, I drag them apart to match the actual physical set up, and click "apply."  Then the settings revert to the one-on-top of the other immediately and so there are no actual changes made (I see the revert dialog).

I tried running it from the console so I could capture any error output:
```

wen@fluffy:~$ gnome-display-properties 

(gnome-display-properties:10940): display-properties-WARNING **: Creating revert dialog


```

Nothing special.  Any ideas how to fix this problem?

---

### Post by thepipirate on 2008-08-24
Let me add that I'm using Hardy, and ask if perhaps I should post this in the "Desktop Environments" forum, as it may be a problem with Gnome instead of Ubuntu.

---

