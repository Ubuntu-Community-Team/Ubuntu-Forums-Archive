---
title: "No xorg.conf - how to change color depth?"
date: 2010-08-04
forum: Multimedia Software
---

### Post by groovy354 on 2010-08-04
I want to change color depth, but there's no xorg.conf file to edit... what to do?
btw, shouldn't there be a simple gui for that? Like for changing resolution

---

### Post by shreepads on 2010-08-04
Ummm sounds impossible if you're running a graphical desktop.

Output of 
```
ls /etc/X11/xorg*
```
plase?

---

### Post by ajgreeny on 2010-08-04
There has not been an xorg.conf by default for the last two or three versions of ubuntu, however, if you run a restricted driver for the card, that file is usually made by the driver.  You can also make such a file manually, but to do so need to know what the card is and more hardware information.  I run an ati 9200SE card and have to have a manually produced xorg.conf to get acceptable (just) performance.

Tell us what card you run and more help may be forthcoming.  To find the card in use run ```
lspci
``` in terminal and report back the output here.

---

### Post by robert shearer on 2010-08-04
Yes, it can be done.
you need to generate an .xorg file then edit it for the colour depth you want.

This post tell you how to create an .xorg....
[http://ubuntuforums.org/showpost.php?p=9362728&postcount=2](http://ubuntuforums.org/showpost.php?p=9362728&postcount=2)
(only use gdm in the commands, for Ubuntu, not xdm thats for xubuntu )


to check your current colour depth run...
```
xdpyinfo | grep "of root"
```


Oh, and for completeness... should changes you make cause Ubuntu to be unable to boot to the desktop then reboot and hold the shift key down after the POST screen.
This will get you to the grub menu where you will select "recovery mode' option and boot to a text login.

After you login run..
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
and then reboot.

That will rename the xorg.conf file and it won't be run at boot so you will be back to the settings you have now.

---

### Post by groovy354 on 2010-08-04
ls: cannot access /etc/X11/xorg*: No such file or directory
I'm running from usb stick, could that be the cause?

---

### Post by ajgreeny on 2010-08-04
> **groovy354 said:**
> ls: cannot access /etc/X11/xorg*: No such file or directory
I'm running from usb stick, could that be the cause?
That will be looking for the xorg.conf of the live USB, so is to be expected.

You do not need to do that anyway as you will not have an xorg.conf if you have not made one or installed a proprietary driver.  What card do you have and what driver is it using?

Follow the link from robert shearer to make a file or do it manually if you prefer, add the colour depth info needed and then restart x.

My xorg.conf contains the following where color depth is set.  Edit this as needed for your system and resolutions and see if it helps.

```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    16
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

---

