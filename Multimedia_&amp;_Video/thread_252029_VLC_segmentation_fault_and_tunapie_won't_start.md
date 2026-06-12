---
title: "VLC segmentation fault and tunapie won't start"
date: 2006-09-06
forum: Multimedia &amp; Video
---

### Post by finferflu on 2006-09-06
Hi all,

I'm facing some problems with two apps, and I'm facing them since I've installed a couple of packages, but the thing is that I don't know which ones are causing the problem.

First of all, this is what I get whenever I try to start VLC:
```
mmanu@ubuntumachine:~$ vlc
VLC media player 0.8.4 Janus
Segmentation fault
```

And secondly, when I try to run tunapie:
```
mmanu@ubuntumachine:~$ tunapie
Traceback (most recent call last):
  File "/usr/share/tunapie/Tunapie.py", line 9, in ?
    import wx
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
    from wx._core import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 13405, in ?
    from _misc import *
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_misc.py", line 4, in ?
    import _misc_
ImportError: /usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_misc_.so: symbol _ZTV11wxLogBuffer, version WXU_2.6 not defined in file libwx_baseu-2.6.so.0 with link time reference
```

I tried to uninstall them (aptitude purge), but after I reinstalled them, I got the same errors.

So, I guess this is something related to some packages I've installed. I have recently installed the ATI drivers with Easyubuntu (but I can't uninstall them with it, and I don't know how to do), Wired and the wired-libs. I have managed to uninstall [Wired]("http://wired.is.free.fr") with [checkinstall]("http://ubuntuforums.org/showthread.php?t=249221"), but I can't uninstall the wired-libs, since I've installed them with a .sh script (and I'm still waiting for a response on their [forums]("http://wired.is.free.fr/userforum/viewtopic.php?p=1229#1229"))

I don't know what to think about, as I am relatively new to Linux, about one year's experience...

Thanks for you time.

---

### Post by finferflu on 2006-09-15
Bump!

Sorry if I bump, but I really would like to have my VLC back (and tunapie as well, if possible)... I managed to uninstall the wired-libs, but still I can't run those programs.

Is there anyone who can give me some hints?


Thanks a lot!

---

### Post by nirudha on 2006-09-15
VLC stopped working for me as well. Get the following error

[INDENT][I]VLC media player 0.8.5 Janus
Segmentation fault[/I][/INDENT]

---

### Post by lunadog on 2006-10-17
Have you tried the new version of tunapie (1.1.1)?

Also, tunapie is now in debian unstable, so it should be in ubuntu soon!

Edit: please contact me directly (author of tunapie) if you have continuing problems ;)

---

### Post by finferflu on 2006-10-17
Thanks a lot for your support, and thanks for creating tunapie! It's a very cool app!

I haven't got any internet connection at home at the moment, but I'll get it in the next week or so... I'll give you updates :) 

Thanks again!

---

### Post by finferflu on 2006-10-30
Well, I had some issues with the upgrade of Dapper, so I had to do a clean install of Edgy. So everything works again!

---

