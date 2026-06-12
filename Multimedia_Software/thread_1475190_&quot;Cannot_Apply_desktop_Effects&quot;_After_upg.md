---
title: "&quot;Cannot Apply desktop Effects&quot; After upgrade"
date: 2010-05-06
forum: Multimedia Software
---

### Post by tylersontag on 2010-05-06
Hey all,

Just upgraded my laptop to 10.04, i've been stringing this baby along for the last 2 years so i think it started at 7.10, so this is by no means a fresh install.

After the upgrade, my custom skin/desktop icons are all gone (but i really don't care about them, that skin was getting old) but what does bug me is that my desktop effects are turned off now.

I miss my cube, i installed some drivers via a deb package posted at the bottom of this bug report [https://bugs.launchpad.net/ubuntu/+bug/565969](https://bugs.launchpad.net/ubuntu/+bug/565969)  but with no noticable difference.

Any ideas?

---

### Post by lidex on 2010-05-06
You know how to enable them, right? So I can assume that didn't work? Follow the compiz-check link in my sig to DL and run the script. Post results here.

---

### Post by tylersontag on 2010-05-07
Looks like that site is not currently up, i got the google cache page but that scripts is stored off page and i couldn't find any sort of mirror, does anyone know of one or could someone post the contents/file?

---

### Post by lidex on 2010-05-07
It's up now.

---

### Post by tylersontag on 2010-05-08
XXX@XXXXX:~/Programs$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by tylersontag on 2010-05-08
i did a dpkg-reconfigure xorg-server and added this section to my xorg.conf

Section "Files"     
    ModulePath      "/usr/lib/xorg/modules"
EndSection

and i could enable it... but now, when i have it enabled, using firefox crashes my firefox everytime i try to run it... fml

---

### Post by tylersontag on 2010-05-10
I think its XORG crashing, i have to login anew after every down, the screen looks 'funny' when it happens and my session is reset.

Does anyone know if theres any sort of XORG error log i can check out?

---

### Post by lidex on 2010-05-11
> **tylersontag said:**
> I think its XORG crashing, i have to login anew after every down, the screen looks 'funny' when it happens and my session is reset.

Does anyone know if theres any sort of XORG error log i can check out?

```
cat /var/log/Xorg.0.log
```

---

