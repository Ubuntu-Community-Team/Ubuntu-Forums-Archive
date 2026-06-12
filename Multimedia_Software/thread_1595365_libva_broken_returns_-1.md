---
title: "libva broken? returns -1"
date: 2010-10-13
forum: Multimedia Software
---

### Post by ridewithstyle on 2010-10-13
Hello folks,

I'm running ATI 4290 integrated graphics, previously 10.04 x64 with manually installed catalyst, self compiled mplayer with vaapi support and libva and xvba from 

[http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)

Everything worked realy fine in 10.04, then I made a mistake.

Yesterday I upgraded to 10.10 (x64) and since then I can't get vaapi running anymore. I'm using the provided fglrx driver, libva1 is part of the main repo, and claims to be newer than the one provided by splitted desktop. I installed xvba from splitted desktop and vainfo from the universe repo and vainfo tells me there is sth missing. 


```
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```

I have crawled through the entire internet trying to find out why libva returns -1. No luck whatsoever. I hesitate to remove the provided libva1 and replace it with the splitted-desktop version, because there a tons of depending programs. 

Any ideas? Anyone? Help would be really appreciated

Greetings, rws

---

### Post by KleeWho on 2010-10-13
Try libva from [http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/]("http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/"). Vainfo works fine with it, and it didn't messed up anything with dependencies (I didn't notice anything)

---

### Post by ridewithstyle on 2010-10-13
thx, that was my first try, but I can't do that. 

Error Message is: a later version is already installed. The later version is the libva from the maverick repo which I can't uninstall without breaking lots of other packages.

Are you running 10.10? 

Greetings, rws

---

### Post by KleeWho on 2010-10-13
Yeah, since yesterday it's Ubuntu 10.10.

Software center indeed gave the "a later version already installed" but I don't get any error messages when I do:

sudo dpkg -i libva_from_gbeauchesne.deb

---

### Post by ridewithstyle on 2010-10-13
ok, that did the trick!

I couldn't uninstall libva, but the commandline overwrite worked perfectly. I had to additionally remove the vainfo package, because the splitted desktop already includes that one. Last thing I had to do was to hold back the upgrade of the packets, as in locking the version. Playback is still not optimal, but mplayer permanently stays under 12% CPU, which is totally acceptable. 

So thanks very much for the tip with shell install, did not know that you can downgrade packages that way. 

Regards, rws

---

### Post by fpga_brad on 2010-10-25
When I try to dpkg I get an error"cannot access archive: No such file or directory". Any ideas what I am missing?

---

### Post by bsmith1051 on 2010-11-05
> **fpga_brad said:**
> When I try to dpkg I get an error"cannot access archive: No such file or directory". Any ideas what I am missing?
I would assume you have the path and/or filename wrong?
________

P.S. Thank you for this thread! I still don't have vaapi working, of course(!), but uninstalling the original 'vainfo' and using that 'dpkg' command-line is the first bit of progress I've made. See my own thread, [http://ubuntuforums.org/showthread.php?t=1614469](http://ubuntuforums.org/showthread.php?t=1614469)

---

