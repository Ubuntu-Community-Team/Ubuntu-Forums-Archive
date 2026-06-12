---
title: "ATI driver breaks Totem"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by Kivech on 2008-03-13
Hi all,

Finally, after a month, I managed to get the ATI drivers to work properly. Now I knew I would face some challenges with the ATI drivers, but this one was a bit unexpected.

Totem used to play basically all streaming perfectly with the proprietary driver that came with Ubuntu and xserver-xgl. With other video apps I found ways to make them work somewhat ok (not always perfectly though). 
After installation of the latest ATI drivers on a fresh Gutsy 64 install I installed all plugins, media players, etc. VLC works after switching to X11 video output, and so does Kino. Unfortunately Totem doesn't have that option in its configuration menu, and it is not playing anything anymore.

When I try to play any type of video file it either crashes instantly or goes all haywire and just shows a black screen with menu items going all over the place, window bars flying all over, etc. It's quite a spectacular sight, but not really what I was looking for. :lolflag:

Anyway, I guess I have two options:

1) Finding a way to get Totem to display in X11 instead of what it uses by default, or
2) Find a different way to have it display streaming video properly.

The ATI drivers I installed are the latest 8.3 version. Lots of things have improved, however Totem really has become completely redundant this way.

Any hints or help would be highly appreciated.

Edit: forgot to mention that when I start totem from the terminal I get this error message:
> sh: jackd: not found
And I get this message when totem crashes:
> The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 54 error_code 2 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Kivech

---

### Post by Kivech on 2008-03-13
Found the fix myself already:
> Press Alt+F2 and type
gstreamer-properties
Select "Video" and in the first section ("Default out" or similar) and switch "Plugin" to "X Window System (without Xv)".

For those that have the same problem.

Kivech

---

