---
title: "Burning xbox 360 backups"
date: 2008-09-07
forum: Multimedia Software
---

### Post by blackvd on 2008-09-07
I'm trying to burn some xbox 360 iso backups I have. First I tried using Nero Linux and just burning them as an DVD ISO file with no success. Second I tried burning them using

```
 growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvdrw=IMAGE.000
```

The first two times it finished but still wouldn't work. The second ISO I tried with that command I received this error:

```
Executing 'builtin_dd if=x360-cod4.iso of=/dev/dvdrw obs=32k seek=0'
:-? Failed to change write speed: 2770->3324
/dev/dvdrw: splitting layers at 1913760 blocks
:-[ SEND DVD+R DOUBLE LAYER RECORDING INFORMATION failed with SK=7h/ASC=00h/ACQ=00h]: Input/output error
```

I'm using Memorex DVD R DL with a TSSTcorp DVD+-RW TS-L632D DVD burner located at /dev/scd0.

Any help would be great as I've gone through 6 disc so far at $2 each.

Here is one of the guides I followed [http://blog.reloadsystems.net/2007/02/02/burning-xbox-360-games-in-linux/]("http://blog.reloadsystems.net/2007/02/02/burning-xbox-360-games-in-linux/")

---

### Post by blackvd on 2008-09-07
Ive also tried all the methods available here:

[http://ph.ubuntuforums.com/showthread.php?t=571961]("http://ph.ubuntuforums.com/showthread.php?t=571961")

Unfortunately cli finishes but doesn't run and k3b just errs out. imgburn will install with wine but doesn't detect my drive. Also tried installing cloneDVD via wine but I get an error when trying to run it. 

WinXP in vmware doesn't detect my drives either.

:confused:

---

### Post by blackvd on 2008-09-07
Finally got imgburn to work in wine by running winecfg and auto detecting my drives. Seemed to burn ok but when i try it I get the same thing "unplayable disc". Sometimes it will go to the media player and give me the "Insert this disc into an xbox 360" 4 second video.

---

### Post by blackvd on 2008-09-09
After all that I finally just brought my work laptop home with Vista on it and burned using imgburn. Worked great the first time. One thing I noticed when coping the large files from my Linux laptop via my USB flash drive is that I get 1 Mb/s transfer when using gnome and 10 Mb/s when using mc. With Vista I get 25 Mb/s!!! Would love to know why that is?

---

### Post by ouija on 2009-02-12
I have created a script that helps simplify burning 360 backups.

see: [http://ubuntuforums.org/showthread.php?t=1068067&highlight=burn+xbox+360+backups](http://ubuntuforums.org/showthread.php?t=1068067&highlight=burn+xbox+360+backups)

---

### Post by JustANewb on 2009-02-16
I don't know if its just Linux not wanting to burn it for you or if it might be the disks.  I have read multiple articles of people being able to use other vendors of dual layer disks with no problem but I bought a spindle of memorexs and they won't burn for anything in Linux but not problem in windoze...  quirky.

---

