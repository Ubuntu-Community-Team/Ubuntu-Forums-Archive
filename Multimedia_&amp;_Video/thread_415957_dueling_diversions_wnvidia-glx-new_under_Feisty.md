---
title: "dueling diversions w/nvidia-glx-new under Feisty"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by jejones3141 on 2007-04-20
I have, after some difficulty, upgraded from Edgy to Feisty. (I had to uninstall tomcat5.5 and apache2, and the repeated backing out of the upgrade generates a LOT of initrd.img-<kernel version> files which filled my probably too-small /boot partition, but it appears to have worked.)

I dropped back to "nv", figuring it would be the safe thing to do.. I have an nVidia 7600 graphics card, so I presume I should use nvidia-glx-new under Feisty... but when I try to install that, I get the following:

dpkg-divert: `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'

I uninstalled nvidia-glx, but still get that message.

I see that I had envy installed, and may have run it to get around the problem of a repository which moved to the newest driver while I had a 4400 (which the new driver no longer supports) installed. Could envy have done something to cause the error message from dpkg-divert?

---

### Post by jejones3141 on 2007-04-20
Looking at the dpkg-divert manual page, it occurs to me that the thing to do is remove the diversions associated with nvidia-glx and nvidia-glx-new. <famous_last_words>Since neither is installed, it should be safe to do so, right?</famous_last_words>

---

### Post by Alain21 on 2007-04-21
Alright ... i have the same exact error .. how did you fix it ... ?? what do you mean by removing the diversion ?? how exactly ??

---

### Post by jejones3141 on 2007-04-21
Actually, I haven't fixed it yet; I'm still confused by the syntax of dpkg-divert.

The salient portions of /var/lib/dpkg/diversions:

/usr/X11R6/lib/libGL.so.1
/usr/X11R6/lib/nvidia/LibGL.so.1.xlibmesa
nvidia-glx
/usr/X11R6/lib/libGL.so.1.2
/usr/X11R6/lib/nvidia/LibGL.so.1.2.xlibmesa
nvidia-glx
/usr/lib/xorg/modules/libGLcore.so
/usr/lib/nvidia/libGLcore.so.xlibmesa
nvidia-glx

(and later on in the file...)

/usr/lib/libGL.so.1
/usr/lib/nvidia/LibGL.so.1.xlibmesa
nvidia-glx-new
/usr/lib/libGL.so.1.2
/usr/lib/nvidia/LibGL.so.1.2.xlibmesa
nvidia-glx-new

I presume I need to run

sudo dpkg-divert --package <package> --remove --rename <pathname> <pathname>

once for each of those pairs, but can someone tell me which pathname goes where, please? "man 5 diversions" gives no documentation, and the only files of the ones mentioned above that exist on my system are /usr/lib/nvidia/libGL.so.1.2.xlibmesa (and /usr/lib/nvidia/libGL.so.1.xlibmesa, a symlink to the other).

---

### Post by Alain21 on 2007-04-21
Im gonna try a fresh install from live cd ... hope it wil help

---

### Post by papabean on 2007-04-21
For dpkg-divert, all I needed to do was use --remove with the appropriate file, for example:

```
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1.2
sudo dpkg-divert --remove /usr/lib/xorg/modules/libGLcore.so
```After that, I was able to install the nvidia-glx driver normally.

Hope this helps.

---

### Post by jejones3141 on 2007-04-21
> **papabean said:**
> For dpkg-divert, all I need to do was use --remove with the appropriate file, for example:

```
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1
sudo dpkg-divert --remove /usr/X11R6/lib/libGL.so.1.2
sudo dpkg-divert --remove /usr/lib/xorg/module/libGLcore.so
```

After that, I was able to install the nvidia-glx driver normally.

Hope this helps.

Yee-haw! That did the trick, save that it took a minute or two of head-beating to realize that you had a minor typo in the third command; it's modules, not module. I mention this only to save others with the same problem I had the bother; having made that correction, the install of nvidia-glx-new went smooth as silk. You, sir, have my eternal gratitude.

---

### Post by papabean on 2007-04-22
> **jejones3141 said:**
> Yee-haw! That did the trick, save that it took a minute or two of head-beating to realize that you had a minor typo in the third command; it's modules, not module. I mention this only to save others with the same problem I had the bother; having made that correction, the install of nvidia-glx-new went smooth as silk. You, sir, have my eternal gratitude.

Thanks for pointing out the typo.  I corrected it so that others may also benefit.  Glad it helped.

---

### Post by brazzmonkey on 2007-04-22
as simple as that. thanks guys !!

---

### Post by jondecker76 on 2007-04-22
aaahhh... great, i was having the same problem!

---

### Post by mefellows on 2007-04-24
I had the same problem after installing Feisty and thanks to jejones3141 it's all fixed. In most respects everything including drivers was automatically installed and worked! I can even use encryption on my wireless network now without all the mucking around i had to do with Dapper and less so Edgy. Love Ubuntu...

---

### Post by Krislarsen on 2007-05-01
Same problem here too, but this fixed it :)

---

### Post by cfreyer on 2007-11-05
In addition to the 3 diversions mentioned above, I had a few moreto add a couple more....

sudo dpkg-divert --remove /usr/lib/libGL.so.1
sudo dpkg-divert --remove /usr/lib/libGL.so.1.2
sudo dpkg-divert --remove /usr/lib/xorg/modules/libglx.so

In retrospect, the easy way to identify all the diversions is:

dpkg-divert --list nvidia-glx-new
or
dpkg-divert --list nvidia-glx
(depending on which package you installed).

---

