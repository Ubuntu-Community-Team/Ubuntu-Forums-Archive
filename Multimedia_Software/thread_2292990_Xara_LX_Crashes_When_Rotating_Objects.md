---
title: "Xara LX Crashes When Rotating Objects"
date: 2015-09-01
forum: Multimedia Software
---

### Post by braznyc on 2015-09-01
Yes, I use Inkscape too... But I need Xara working.
It happens when I use the rotating handles.

It started when I upgraded Ubuntu to the latest versions!


Any help is welcome!

---

### Post by tgalati4 on 2015-09-02
Welcome to the forums.  What version of Ubuntu are you running?

Open a terminal and run *xaralx* it with a debug switch:

```
xaralx --debug
```

Since *xaralx* is an older code base, perhaps try running in an older version of Ubuntu, such as 12.04 or 10.04 (which is out of support).  

Some history:  [http://ubuntuforums.org/showthread.php?t=1907117](http://ubuntuforums.org/showthread.php?t=1907117)

---

### Post by braznyc on 2015-09-02
I'm using Ubuntu 15.04.

I've noticed it was last updated on 19-Jul-14. Which is pretty recent. So it is still active. :popcorn:


More info:

Xara Xtreme
Version: 0.7 ()
Build date: 19-Jul-14 18:07
Built against: wxWidgets 2.8.12
Usage: xaralx [xar-file...]



This is what I get when I run 

[COLOR=#000000][FONT=Ubuntu Mono]xaralx --debug



[/FONT][/COLOR]Usage: xaralx [-h] [-v] [-r <str>] [-x] [input file...]
  -h, --help            Display this help
  -v, --version         Display the version information
  -r, --resource=<str>  resource directory
  -x, --xrccheckgen     generate xrc.check file
Unknown long option 'debug'



Thanks.

---

### Post by tgalati4 on 2015-09-03
So run it in the terminal without any switches and rotate some objects.  Post the errors that show up in the terminal after the crash.

---

### Post by braznyc on 2015-09-03
(xaralx:7537): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:7537): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:7537): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:7537): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:7537): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:7537): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed
Aborted



Nothing changes when it crashes... The "aborted" line is added because the program asks to be closed to try to save the work.

---

### Post by Silexy on 2015-09-20
Yesterday I installed Xara Xtreme on Ubuntu 14.04 LTS, and tried to draw something.
I had the same experience as Braznyc when rotating an object. (Work lost, for I didn't save.)
Another thing I encountered are error messages when exporting parts of a drawing as JPG or PNG.
The images were saved, though.

Perhaps it is enevitable that we have to say Goodbye to Xara on Linux or Ubuntu, as Linux keeps getting upgraded, and Xara is not supported anymore.
That would be a real pity.

---

### Post by tgalati4 on 2015-09-20
It's true the frameworks that Linux is built on are constantly changing.  Does someone have xaralx running on 12.04 to test rotating objects?

---

### Post by braznyc on 2015-09-24
> **tgalati4 said:**
> It's true the frameworks that Linux is built on are constantly changing.  Does someone have xaralx running on 12.04 to test rotating objects?


The rotation works on Ubuntu 12.04. There's another bug that appears on 12.04: Xara LX has no menu. You have to use the keyboard to access the menu.

---

### Post by Silexy on 2015-09-27
> **braznyc said:**
> The rotation works on Ubuntu 12.04. There's another bug that appears on 12.04: Xara LX has no menu. You have to use the keyboard to access the menu.

The rotation of Xara also works on Mint 17.2. 
I installed Mint on the same computer and next to Ubuntu 14.04.

---

### Post by tgalati4 on 2015-09-27
It does not work on Linux Mint MATE 17 (based on 14.04).  I get a segmentation fault when I try to rotate a rectangle.  When I select "Generate Error Report", no report is written.  I get the same error messages in the console as braznyc.  The only difference is I get "Segmentation fault" instead of "aborted".

Someone needs to file a bug against xaralx and 14.04.  That would be a better candidate for support than 15.04.

---

### Post by Portaro on 2015-09-28
Itry here I have Lubuntu 14.04 -

> joao@P4V88:~$ xaralx

(xaralx:25944): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:25944): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:25944): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:25944): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:25944): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:25944): Gdk-CRITICAL **: IA__gdk_window_get_origin: assertion 'GDK_IS_WINDOW (window)' failed


(xaralx:25944): Gtk-CRITICAL **: IA__gtk_range_set_range: assertion 'min < max' failed


(xaralx:25944): Gtk-CRITICAL **: IA__gtk_window_set_modal: assertion 'GTK_IS_WINDOW (window)' failed


(xaralx:25944): Gtk-CRITICAL **: IA__gtk_window_set_modal: assertion 'GTK_IS_WINDOW (window)' failed




Xara Xtreme
Version: 0.7 ()

I can export but I receive this error -> 

[[IMG]http://s25.postimg.org/ag8i6ys0b/2015_09_29_005559_1280x1024_scrot.jpg[/IMG]]("http://postimg.org/image/ag8i6ys0b/")
[[img]http://s25.postimg.org/9f89hub0r/2015_09_29_010328_1280x1024_scrot.jpg[/img]](http://postimg.org/image/9f89hub0r/)

I try to rotate the content and I only rotate to right and left and for me works.

I have Nvidia FX 5500 drivers installed , maybe the problem is the graphic cards and maybe - LIBGL_ALWAYS_SOFTWARE=1 can help to try to solve the problem (but is an idea).

---

### Post by braznyc on 2015-09-28
> **Portaro said:**
> Itry here I have Lubuntu 14.04 -



Xara Xtreme
Version: 0.7 ()

I can export but I receive this error -> 

[[IMG]http://s25.postimg.org/ag8i6ys0b/2015_09_29_005559_1280x1024_scrot.jpg[/IMG]]("http://postimg.org/image/ag8i6ys0b/")
[[IMG]http://s25.postimg.org/9f89hub0r/2015_09_29_010328_1280x1024_scrot.jpg[/IMG]]("http://postimg.org/image/9f89hub0r/")

I try to rotate the content and I only rotate to right and left and for me works.

I have Nvidia FX 5500 drivers installed , maybe the problem is the graphic cards and maybe - LIBGL_ALWAYS_SOFTWARE=1 can help to try to solve the problem (but is an idea).



Ignore the "error message"... The file is saved anyway. It happens when you save the image as a PNG.


It could be the graphic cards. My card is an Intel.

---

### Post by coffeecat on 2015-09-30
*Thread moved from Art & Design to **Multimedia Software**.*

*Art & Design* forum tagline:

> Discuss various aspects of Ubuntu and Art here. Questions about using software for image editing should go in the Multimedia Software section.


---

