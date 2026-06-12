---
title: "mplayer dont work after some flash played such as youtube ?"
date: 2009-10-11
forum: Multimedia Software
---

### Post by iblicf on 2009-10-11
hi, everybody

it's so strange ..that, when i see some movie in such as youtube using browser (firfox ) , then my mplayer will not work again (it just stay the frame of some screen  ) ,so i must reboot , or logout .  what's wrong ?

somebody met this ever ? and how can i deal with this ?
thanks a lot ! ubuntu 9.04

---

### Post by laceration on 2009-10-12
Not that you are...but don't blame it on MPlayer.  Flash is infamous for causing problems, especially if you have a 64-bit system.  Usually you can avoid problems if you close your browser before opening MPlayer.  MPlayer can be stubborn to close but you shouldn't have to reboot or log off.  At a command line you can
```
$ killall mplayer
```
or you can close it from the System Monitor.

---

