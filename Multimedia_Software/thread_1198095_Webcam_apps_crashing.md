---
title: "Webcam apps crashing"
date: 2009-06-27
forum: Multimedia Software
---

### Post by uvdevnull on 2009-06-27
Since upgrade to Jaunty, apps like ekiga and cheese are crashing when accessing the Logitech webcam stream (UVC). 

No idea where to start looking for clues... :confused:

---

### Post by tolotos on 2009-06-27
Well it would be very helpfull, if you could post some error massages. For example you could try to start cheese and ekiga in the console, an paste their output(if any) here. Also it might be usefull to post the output of "dmesg | tail", just after you plugged in your webcam.

---

### Post by uvdevnull on 2009-06-27
Furthermore, I'm also now unable to play avi video files using Totem or VLC, they crash immediately when playback starts. Only MPlayer plays them. 

Utilities like gstreamer for example record fine from command line, but crash when trying to view the stream live.

This all seems related...

---

### Post by uvdevnull on 2009-06-27
[~]$ cheese
The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 70 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

[~]$ ekiga
The program 'ekiga' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 48 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

(ekiga:10751): Gdk-CRITICAL **: gdk_drawable_get_size: assertion `GDK_IS_DRAWABLE (drawable)' failed


[~]$ totem test1.avi
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 85 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Common thread seems to be:
```

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
(Details: serial ## error_code 11 request_code 132 minor_code 19)
```

---

### Post by uvdevnull on 2009-06-27
In light of the new findings, I'm thinking this problem is probably unrelated to the webcam.  The apps still crash without it even connected.

---

### Post by tolotos on 2009-06-27
Your problem is indeed unrelated to your webcam. The cause of your trouble is a bug in a certain version of the xorg-server. You should at first try 
sudo apt-get update
sudo apt-get upgrade
and restart your computer.
If this doesn`t help you could try a downgrade to a prior version via:
sudo apt-get install xserver-xorg-core=2:1.5.2-2ubuntu3 && dpkg-reconfigure xserver-xorg-core
Furthermore datails related to your problem can be found at : 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/360524](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/360524) (thats where I got the downgrade tip)
or at:
[http://www.linux-club.de/viewtopic.php?t=90313](http://www.linux-club.de/viewtopic.php?t=90313)
Hope that helps

---

### Post by uvdevnull on 2009-07-11
Solved the problem following this guide:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
I just did the "Safe" option.

---

### Post by pwebster25 on 2009-07-16
I have the same problem with my internal webcam on an Acer Aspire One netbook.  I'm afraid to do the solution suggested, even the safe one, as everything else on the netbook works great (everything that doesn't involve the webcam).  Oddly enough, when I first installed Jaunty (still in beta or RC at the time) the webcam and cheese worked great.

---

### Post by uvdevnull on 2009-07-16
> **pwebster25 said:**
> I have the same problem with my internal webcam on an Acer Aspire One netbook.  I'm afraid to do the solution suggested, even the safe one, as everything else on the netbook works great (everything that doesn't involve the webcam).  Oddly enough, when I first installed Jaunty (still in beta or RC at the time) the webcam and cheese worked great.

Hey brother,
It's worth a try, imho. There are instructions in the same guide to revert any changes if for some reason it makes things worse for you.

---

