---
title: "Problem with Totem-xine"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by luisjorge on 2007-08-16
Hello!

I've been using Totem-xine for about a month now, and have played almost every type of file I could find in my hard disk, and everything without a problem.

Today, out of nowhere, totem doesn't work properly. If I open it on its own, it's fine, until I open a file. No matter which type it is, it closes before playing a second.
Same thing if I try to open any file from nautilus.

I have switched back to gstreamer totem, which works fine, but I like more the video quality I got in xine.
Does anyone have an idea on what could be happening?

Thanks very much in advance!

Luis Jorge

---

### Post by RomeReactor on 2007-08-16
Hi. Try opening it through the terminal (Applications->Accessories->Terminal) by entering:
```
totem
```
and open a video file; if totem crashes, please post any output left in the terminal.

---

### Post by luisjorge on 2007-08-17
Hi!
Thanks for the quick reply! I opened totem from the terminal and, when opening a video, closed itself. I got this:

luisjorge@ubuntu-inspiron:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Any ideas?

Thanks in advance!

---

### Post by RomeReactor on 2007-08-17
Do you have an Intel video card? are you running Desktop Effects (Compiz) or Beryl? if so, take a look at [this entry in UbuntuGuide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback"). This issue might be related to [this bug]("https://bugs.launchpad.net/xorg-server/+bug/111257").

---

### Post by luisjorge on 2007-08-18
Hi!

Thanks for helping!
Yes, I have an Intel 915GM card, and using Beryl. Thanks for the links, as well! I checked them and used the workaround there for gstreamer-totem, and it works. I switched from the 915resolution fix + xserver-xorg-video-i810 (combination which worked with totem-xine AND beryl working), to the xserver-xorg-video-intel driver and the problems began. I'd switch back to the first drivers combo, but then my monitor doesn't turn back on if I close the lid of my laptop and then open it, and then I have to do a hard-reboot.

I can play movies on totem-gstreamer for the moment, with the workaround found in the links you said, but the video quality is quite poor and the player eats up processor power like it didn't before... Do you know of any solution to this? Or do I get used to turn of beryl when playing a movie?

Thanks for the help!!

---

