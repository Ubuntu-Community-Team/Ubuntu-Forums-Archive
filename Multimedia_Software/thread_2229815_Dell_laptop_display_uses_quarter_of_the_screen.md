---
title: "Dell laptop display uses quarter of the screen"
date: 2014-06-15
forum: Multimedia Software
---

### Post by Mike_Walsh on 2014-06-15
Afternoon all.

Now, I'm aware this is a rehash of some existing threads, but since the suggestions in those haven't worked for me, I'm hoping giving some extra info in the right forum may yield some results.

I have a 2003 Dell Inspiron 1100 laptop, on which I've just installed Lubuntu 14.04. The O/S is working fine; however, I'm stuck with a 640x480 display in the top left quarter of the screen. Monitor Settings offers no other options.

I've read this thread about my problem:- [http://ubuntuforums.org/showthread.php?t=2222349](http://ubuntuforums.org/showthread.php?t=2222349)
                                 and also this:- [http://ubuntuforums.org/showthread.php?t=2222014](http://ubuntuforums.org/showthread.php?t=2222014)

Doranwen in the first thread has got exactly my model and same hardware, so I followed this through. At the bottom of the first post, his solution has been added; I tried this, but the 'i845.modeset=0' didn't work for me. So I tried the 'nomodeset' option, and, following Morgaes advice in this thread ([http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)) I've edited the grub bootloader, and rebooted.

I now have the same 640x480 display, but in the centre of the screen, with a black border round it.

Reading further through the forums, I came across this thread: [http://ubuntuforums.org/showthread.php?t=2222014](http://ubuntuforums.org/showthread.php?t=2222014). I've run the 'xrandr' command through the terminal, and the output is as follows (bear with me, for some reason I can't copy this, so I'm typing it instead...)

mike@mike-Inspiron-1100:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640 x 480+0+0 0mm x 0mm
   640x480          73.0*
mike@mike-Inspiron-1100:~$

Hope that makes sense; I've copied it as closely as possible.

Anybody got any ideas? Or further advice? I really don't know quite where to go from here...

Mike.

---

