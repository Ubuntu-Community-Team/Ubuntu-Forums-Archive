---
title: "Older Laptop Monitor"
date: 2008-12-20
forum: Multimedia Software
---

### Post by subversus on 2008-12-20
Hi All,

A friend of mine has installed Ubuntu linux on an older Toshiba A25-s207 laptop. The system runs great, except for one problem: the screen display does not fill the entire physical monitor space. His monitor will support 1024x768 resolution, but this system will only display 800x600 in a small box in the center of the screen. It's like the OS display has margins of blank space. 

I've seen this problem before, but I never knew how to fix it. I tried searching, but it's difficult to describe this problem in a way easily queried. 

Has anyone any idea how to solve this problem?

Thanks,

---

### Post by StevenHarper on 2008-12-20
It may be that the driver found doesn't support the resolution:

However you can try to force the monitor to 1024x768

Ok ready : what your about to do is modify the file that the X server uses : if you break this file, you will have to fix it from a terminal or a Live CD.

Ok lets open a terminal and run the command

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_BACKUP
```

this has backed up you current config
now do this to edit the config

```
sudo gedit /ect/X11/xorg.cof
```

Find this part of the file

```
SubSection "Display"
..............
..............
..............
EndSubSection
```

And change it to 

```
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
```

Double check that you have not added any double lines of Subsection or EndSubsection 

Now save the file and re-start gnome

```
sudo /etc/init.d/gdm restart
```


If you get stuck at a blank screen (login screen)

You can use CTRL+ALT+F2 or any F key (F7 is the gnome one F8 is the bootup) to swap to another text based login (F7 gets you back to the gnome one)

You can then put back the backup file

```
sudo cp /etc/X11/xorg.conf_BACKUP /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

good luck

---

### Post by mobileuser1 on 2008-12-20
I am having the same problem as the one you just responded.  I tried the lines of code that you had suggested, but in the file /ect/x11/xorg.conf the gedit file was blank.  Do you have any suggestions?

I am using Toshiba Satellite P3 1GHZ, Cyberblade XP ai1 display driver.

---

### Post by subversus on 2008-12-20
We tried that too, but it didn't work.

Your xorg.conf file shouldn't be blank. Are you sure you opened it in the right directory?

Also, there was no existing subsection "display" in our file. We put it under the main section "screens," but it gave us assorted errors. With all of those options, as suggested, it dropped the screen resolution to 640x480. When we removed all options except 1024x768, it returned to normal, 800x600. 

I saw this problem once many years ago, and then I saw a fix for it a few years later, but it's been a long time, and now I can't remember how to fix it. =[

---

### Post by overdrank on 2008-12-21
> **mobileuser1 said:**
> I am having the same problem as the one you just responded.  I tried the lines of code that you had suggested, but in the file /ect/x11/xorg.conf the gedit file was blank.  Do you have any suggestions?

I am using Toshiba Satellite P3 1GHZ, Cyberblade XP ai1 display driver.

/ect/x11/xorg.conf  that is a capital X in the X11
```
gksu gedit /etc/X11/xorg.conf
```
If you are using Hardy 8.04 you may try the command ```
gksu displayconfig-gtk
``` and adjust the resolution.

---

