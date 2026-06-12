---
title: "Shotwell and image viewer not working after Gimp 2.8 install"
date: 2012-04-14
forum: Multimedia Software
---

### Post by orange2k on 2012-04-14
Like the title says I'm not able to open shotwell or image viewer after Gimp 2.8 RC install. 

Maybe it has something to do with the new packages installed with the new Gimp?

Has anyone tried the new Gimp and experienced the same problem?

I'm using Ubuntu 11.10...

when I try to open shotwell in the terminal it says:

```
(shotwell:5848): GLib-GObject-CRITICAL **: Read-only property 'read-only-view' on class 'GeeAbstractList' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeList' of the property on the interface 'GeeList'


(shotwell:5848): GLib-GObject-CRITICAL **: Read-only property 'read-only-view' on class 'GeeAbstractSet' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeSet' of the property on the interface 'GeeSet'


(shotwell:5848): GLib-GObject-CRITICAL **: Read-only property 'read-only-view' on class 'GeeReadOnlySet' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeSet' of the property on the interface 'GeeSet'


(shotwell:5848): GLib-GObject-CRITICAL **: Read-only property 'read-only-view' on class 'GeeReadOnlyList' has type 'GeeCollection' which is not equal to or more restrictive than the type 'GeeList' of the property on the interface 'GeeList'

shotwell: symbol lookup error: shotwell: undefined symbol: gtk_window_set_has_resize_grip
```

---

### Post by mc4man on 2012-04-14
How did you go about getting 2.8 on 11.10 (build or ppa
(it's likely the new libs are the issue

---

### Post by orange2k on 2012-04-15
> **mc4man said:**
> How did you go about getting 2.8 on 11.10 (build or ppa
(it's likely the new libs are the issue

I did: 

```
    sudo add-apt-repository ppa:otto-kesselgulasch/gimp

    sudo apt-get update

    sudo apt-get install gimp

```

---

### Post by orange2k on 2012-04-15
I solved the problem by installing GPicView...

---

### Post by machuidel on 2012-04-15
I did the following in a terminal (after removing the gimp PPA):

sudo dpkg --force-all --purge libglib2.0-0 libglib2.0-bin libgdk-pixbuf2.0-0 libgegl-0.0-0 libglib2.0-dev libgtk2.0-common libgtk2.0-bin libgtk2.0-0 libglib2.0-data libglib2.0-0:i386 libgimp2.0 libgegl-0.2-0 libgdk-pixbuf2.0-common libgdata13 libgdata-common libgail18 libgail-common gimp gimp-data gir1.2-pango-1.0 gir1.2-gtk-2.0 gir1.2-gdkpixbuf-2.0 evolution-data-server evolution-data-server-common

And then:

sudo apt-get install libglib2.0-0 libglib2.0-bin libgdk-pixbuf2.0-0 libglib2.0-dev libgtk2.0-common libgtk2.0-bin libgtk2.0-0 libglib2.0-data libglib2.0-0:i386 libgdata13 libgdata-common libgail18 libgail-common gir1.2-pango-1.0 gir1.2-gtk-2.0 gir1.2-gdkpixbuf-2.0 evolution-data-server evolution-data-server-common libpango1.0-0

---

### Post by MrWylbur on 2012-04-17
This is not clear, did you get shotwell working again with Gimp 2.8?

---

### Post by MrWylbur on 2012-04-17
Just figured this out.  Just install the newest Shotwell from the Yorba ppa, instead of the version provided with Ubuntu 11.10:

$ sudo add-apt-repository ppa:yorba/ppa
$ sudo apt-get update
$ sudo apt-get install shotwell 

Instructions here for installing the latest version of Shotwell:
[http://yorba.org/shotwell/install/#binaries](http://yorba.org/shotwell/install/#binaries)

---

### Post by MrWylbur on 2012-04-19
> **MrWylbur said:**
> Just figured this out.  Just install the newest Shotwell from the Yorba ppa, instead of the version provided with Ubuntu 11.10:

$ sudo add-apt-repository ppa:yorba/ppa
$ sudo apt-get update
$ sudo apt-get install shotwell 

Instructions here for installing the latest version of Shotwell:
[http://yorba.org/shotwell/install/#binaries](http://yorba.org/shotwell/install/#binaries)

I take part of this back.  Shotwell is working, but Image Viewer is not.  :(

---

### Post by stevedude on 2012-04-20
I just want to weigh in and state I have the EXACT same problem after using the same PPA. Shotwell works but the EYE OF GNOME (EOG) - The default image viewer for Ubuntu, does not work at all. 

Running eog from the command line, IE: eog something.png results in the terminal just hanging, no output is given at all.

* EDIT * I edited my /usr/share/applications/defaults.list file and installed gThumb instead (which I actually like better).

---

