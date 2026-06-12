---
title: "Msft LifeCam VX-3000 Poor Image Quality  11.10"
date: 2011-10-14
forum: Multimedia Software
---

### Post by koftis on 2011-10-14
I  have the following webcam"* **Microsoft Corp. LifeCam VX-3000***" 
it does not work properly,
I'm running **11.10**, the image and video quality are very poor.

the quality is worse than it was before i have upgraded to 11.10 (swiched from 11.04).

the quality is bad in both **cheese and skype.**
any suggestions?

[COLOR=Red]i'm getting the following error

 **libv4l2: error allocating conversion buffer**[/COLOR]


my specs in 11.04 was[ http://ubuntuforums.org/showthread.php?t=993262&page=9]("http://ubuntuforums.org/showthread.php?t=993262&page=9")

faults in 11.10 
(skype:4977): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:4977): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:4977): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:4977): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
libv4l2: error allocating conversion buffer


Thx in Advance!:lolflag:

---

### Post by EliasYFGM on 2011-10-25
Hello, I am having the same exact problem with my LifeCam VX-3000.

The image quality looks way too blurry with a poor refresh rate. It used to work pretty well in Win7.

Any suggestions? Hoping someone will help on this :)

---

### Post by perat on 2011-11-02
I have the same problem after upgrade to 11.10 (x64).
in cheese: The image is distorted, red streaks, wrong colors.
$ lsusb
Bus 002 Device 002: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000

$ lsmod
gspca_sonixj           33398  0 
gspca_main             28314  1 gspca_sonixj
videodev               93004  1 gspca_main
v4l2_compat_ioctl32    17083  1 videodev

---

