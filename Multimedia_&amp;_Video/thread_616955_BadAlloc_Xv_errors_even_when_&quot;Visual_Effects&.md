---
title: "BadAlloc Xv errors even when &quot;Visual Effects&quot; are DISABLED"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by EXrider on 2007-11-18
I did a fresh install of Gusty on my laptop here, it's a Dell Inspiron 8000 with the SXGA+ display and 32MB ATI Rage M4 Mobility.  

I'm having numerous problems with video playback.  I dug around on the forums here and found others with similar problems, but theirs were all related to ATI and Intel drivers with "Visual Effects" running, so simply disabling them resolved their problem.  Obviously, Compiz isn't supported on this chipset, so it's already disabled.

MythTV plays the small previews as I navigate between recorded shows, but when I play one (or live tv), I get a dark blue screen (or box depending on aspect ratio) with just sound.

Totem and VLC crash as soon as I open a video.  Xine doesn't even launch without displaying a box of garbage and crashing before I can even do anything.  Launching them from the terminal gives me a similar error for each one...

```
me@ubuntu:~$ vlc 
VLC media player 0.8.6c Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
me@ubuntu:~$ xine
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
AFD changed from -2 to -1
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  2544
  Current serial number in output stream:  2545
me@ubuntu:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 56 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

If I config the players to not use Xv, it works, but they drop frames like crazy and use 100% CPU.

Everything had been working flawlessly in Feisty, I'm tempted to switch back now. :confused:

---

### Post by EXrider on 2007-11-20
Nobody has any ideas eh?

---

### Post by EXrider on 2007-11-26
I booted off of the Gutsy CD, at the default 800x600 resolution the videos played fine.  

So I've found that using the newfangled "Screens and Graphics" control panel to set my display to the seemingly correct *"Dell 1400x1050 laptop display panel"*, or *"Generic 1400x1050 LCD Panel"*, or even *"Generic Monitor 1400x1050"* results in the broken Xv output, and BadAlloc errors.  Something about all the modelines it adds, the POS ATI driver (or Xorg) doesn't like I guess?

Starting with the plain xorg.conf booted from the CD, I added the options just as I had done in Feisty, [according to this thread]("http://ubuntuforums.org/showthread.php?t=167670#post977236"), and video suddenly worked just as it did back in Feisty!  So I went ahead and copied that xorg.conf over to my hard drive and booted from it.

Now, booted from the HDD I have video....  that's black and white rrrrgh!  :mad:

Perhaps the Black & White video issue is kernel related...

---

### Post by EXrider on 2007-11-26
Nope, the kernel version is the same on the CD as my installation on the HDD...

So I booted off the HDD in "recovery mode" and startx...  video played correctly with color, same as the CD, so I rebooted again with my normal kernel options and video magically works...  for now.

I have a feeling this problem will return.

---

