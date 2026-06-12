---
title: "gtkam permissions issue"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by maclenin on 2007-03-14
**A. Issue**

1. I have installed (in Edgy Eft (2.6.17-11-generic))...

**gtkam 0.1.3** with options: i486-linux-gnu-gcc, no bonobo, no gnome, no gimp (though I do have gimp installed, separately), exif
**libgphoto2 2.3.0** with options: gcc, no ltdl, EXIF
**libgphoto2_port 0.7.0** with options: gcc, in ltdl, USB, serial without locking

...and had been able to run gtkam (from the desktop "applications" menu) and download photos from a camera, without error - until recently.

2. I now receive the following error message...

> An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

...after I run...

```
gtkam &
```

...from the terminal (or run gtkam via the desktop "applications" menu), with a camera attached - and am unable to access the camera / download photos.

3. I do NOT receive an error message when I run...

```
sudo gtkam &
```

...from the terminal, with a camera attached - and am able to access the camera and download photos.

**B. Background**

With reference to a number of additional posts/bug report(s) (in no particular order)...

1. [http://ubuntuforums.org/showthread.php?p=2105724](http://ubuntuforums.org/showthread.php?p=2105724)
2. [https://launchpad.net/ubuntu/edgy/+source/libgphoto2/+bug/67532/+viewstatus](https://launchpad.net/ubuntu/edgy/+source/libgphoto2/+bug/67532/+viewstatus)
3. [http://lists.debian.org/debian-user/2005/08/msg01447.html](http://lists.debian.org/debian-user/2005/08/msg01447.html)

...I am experiencing a similar error, but feel the nature of my problem transcends the "solutions" I've been encountering. With particular reference to [_post 1._]("http://ubuntuforums.org/showthread.php?p=2105724"), and the solution recommended, therein - I already have the requisite...

```
lsusb
```

...-defined "Vendor id" and "Product id" characters...

```
SYSFS{idVendor}=="lsusb-defined Vendor id", SYSFS{idProduct}=="lsusb-defined Product id", MODE="0660", GROUP="plugdev"
```

 ...incorporated into my...
```

/etc/udev/rules.d/45-libgphoto2.rules
```

...file.

**C. Question**

My thought is that certain permissions/ownership adjustments may have occurred in concert with recent security upgrades, which are preventing me from running gtkam via my "username" (but allowing me to run gtkam as root).... Might there be a way to examine/modify my "username" permissions as they relate to my access to gtkam?

An examination of plugdev - which seems to, possibly, be in play here (from a permissions standpoint, based on _[post 3.]("http://lists.debian.org/debian-user/2005/08/msg01447.html")_), shows my "username" as being a member of that group....

Any thoughts - as to the source/fix of/for this issue?

---

### Post by maclenin on 2007-03-23
Any thoughts?

---

### Post by maclenin on 2007-03-31
Still wondering....

---

### Post by penguin007 on 2007-04-27
See [http://ubuntuforums.org/showthread.php?t=340271](http://ubuntuforums.org/showthread.php?t=340271)

May help

---

### Post by maclenin on 2007-04-29
Thanks, penguin007. I take a look....

---

### Post by MST3Kakalina on 2007-12-13
I'm having the same problem, tried the fix in the thread and it didn't work.

Seems to be related to the latest glibphoto upgrade (or the like), I've never had this problem before.

Any other suggestions?

---

### Post by maclenin on 2007-12-13
To be honest, I have not used gtkam in a long while (and did not pursue a solution to the problem, much beyond my previous post), as my camera (Nikon D50) has the ability to function as a USB drive - so, I just move my photos from the camera, using the resident file manager.... Sorry I can't be of any additional help! Good luck with your search - and if you do find a solution, please post it here!

---

### Post by MST3Kakalina on 2007-12-13
If there's a way to force downgrade glibphoto2, that might solve it.  Dick around in synaptic.  I'm in the middle of finals right now, but if I have the time over break I'll tweak that a bit.


A real-life "workaround" would simply be to use memory cards for all of your picture taking, I imagine.

---

### Post by MST3Kakalina on 2007-12-14
Just as I suspected!  I added a repo to my sources.list (I think it must have been "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main") that upgraded libgphoto from 2.1 something to 2.3.

If the tutorial linked to in here doesn't work for you, this should.

1. Go to Synaptic Package Manager.  Click "Search" and search for photo.

2. Some packages with libgphoto in the name should turn up.  I have "libgphoto2-2," "libgphoto2-2-dev" and "libgphoto2-port0."  Select all of them, and go to Package -> Force Version.  

3. In the dialog box that pops up, you'll have a pulldown menu with the package versions available.  2.3 is probably selected, and you want 2.1.  Select that and hit the "Force Version" button.  The dialog box will close.

4. Select the "Apply" button in the main Synaptic menu.

5. Quit.  You'll be asked in a window if you want to apply the most recent changes.  There will be an option about DOWNGRADING or something similar, select that and confirm the decision.

That should have forced the libgphoto version to the most recent one that still works.  Open up gtkam just to be sure.

---

### Post by maclenin on 2007-12-20
Thanks for the info, **MST3Kakalina**.... I am sure your findings will prove helpful. Again, as I have found success in just treating my camera as a USB drive - and clicking and dragging photos from the camera to the computer, with the file manager - I am all set...and probably won't venture back to gtkam - for a long while! However, should I decide to head back, I'll know where to stop first!

I trust the exams went well....

Enjoy the holiday.

---

