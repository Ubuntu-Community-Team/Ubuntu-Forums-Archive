---
title: "Viewsonic 22&quot; wide screen blues"
date: 2008-11-28
forum: Multimedia Software
---

### Post by michael37 on 2008-11-28
[INDENT]*Headnote to experts: the problem is mostly solved in a brute-force way.  An elegant solution is appreciated.*[/INDENT]

I recently upgraded my old monitor with Viewsonic 22" widescreen monitor.

Once I connected the monitor, Ubuntu recognized the monitor but kept the resolution at the old small one.

OK, so I ran the magic utility
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and restarted X.  The utility configured my xorg.conf to be a simple one as described in [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy).

I restarted X and arrived to a black screen with "out of range" message on the monitor.  OUCH.

The key of the problem is faulty EDID information supplied by the monitor.

```
$ sudo xresprobe -
id: VA2226w-11
res: 1680x1680 1680x1050 1600x1200 1280x1024 1280x960 1152x864 1024x768 832x624 800x600 720x400 640x480
freq: 30-82 50-75
disptype:

```

But the monitor actually does not support 1680x1680 resolution!  My card does, and that's what it sends to the monitor.

Luckily, I had an old trusty xorg.org from old Ubuntu with most of the stuff specified for my old monitor.  I simply modified it match the new monitor's HorizSync, VertRefresh (the are listed above in the freq: output), and created a "Modes" line in Screen/Display without 1680x1680 specification.

From xorg.conf:
```

        Monitor         "VA2226w-11"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

```

Restarted X, everything works.

Questions.
[LIST=1]
[*]My tty (text) modes are still showing up "out of range".  How can I fix them?  The tty modes show up by pressing Ctrl-Alt-F1
[*]How would a non-expert user troubleshoot this problem?
[*]Where to post the how-to about this problem?
[/LIST]

---

### Post by michael37 on 2008-12-10
Bump -- the text modes are still not working for me, and the boot-up sequence doesn't show up until X starts.

---

### Post by element_G on 2008-12-10
just an idea but would this be remedied by putting vga=771 at the end of your boot line in your grub's menu.lst ?? 

you can also use startupmanager to fiddle with the screen res. at boot-up (before X starts)

---

### Post by michael37 on 2009-01-04
> **element_G said:**
> just an idea but would this be remedied by putting vga=771 at the end of your boot line in your grub's menu.lst ?? 

you can also use startupmanager to fiddle with the screen res. at boot-up (before X starts)

No change.  I checked dmesg and verified that vga parameter was passed to kernel during the bootup.

I suspect my "out of range" problem has something to do with "splash" but I don't know how to manage splash.

---

