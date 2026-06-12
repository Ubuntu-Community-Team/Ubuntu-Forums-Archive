---
title: "re-build X server?"
date: 2008-05-15
forum: Multimedia Software
---

### Post by FoX_HunteR on 2008-05-15
i was told my X server was all screwed up, how do i re-build it?

---

### Post by Patb on 2008-05-15
Fox, try this in a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then reboot.  

If it doesn't work, post the details.  

Cheers, Pat.

---

### Post by FoX_HunteR on 2008-05-15
ok cheers, how can i tell if it worked or not?

---

### Post by Patb on 2008-05-15
Fox, if your screen looks okay and your keyboard works as it should, your xserver is definitely not "all screwed up".  If it is relevant, you might post the reasons why someone thought it was.  

Cheers, Pat.

---

### Post by FoX_HunteR on 2008-05-15
someone said it was because of all the driver problems iv been having, i cant for the life of me get the radeonhd drivers to work, it just does not see them no matter what i do...

---

### Post by Patb on 2008-05-16
Fox, I know nothing about radeonhd.  Two suggestions however: 

1.  Try to reconfigure without the -phigh option:
```
sudo dpkg-reconfigure xserver-xorg
```
This will prompt you for different options which you can try.  Keep a backup copy of your xorg.conf first.  

2. If that doesn't work, drop this thread and bump your post at:
[http://ubuntuforums.org/showthread.php?t=795138](http://ubuntuforums.org/showthread.php?t=795138)

I'm not sure whether it will help, but you might explain (on that thread, not here) what you did when:
> I re-built the xserver thingy
(I thought that was what we were discussing here.)  

You might also get something more if you give more details of what your display is missing: 
> It seems to be ignoring it completely

(Sorry if I have misunderstood something obvious).

Cheers, Pat.

---

