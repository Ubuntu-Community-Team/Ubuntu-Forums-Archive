---
title: "Should I Deinterlace My Videos?"
date: 2009-01-31
forum: Multimedia Software
---

### Post by umechanism on 2009-01-31
I have a Sony Hi8 digital video recorder and I'm encoding one full hour of video from this camera.  I'm using Kino for capture, editing, and exporting.

I captured the video in AVI format.  The first DVD disc that I made played well but the image quality was - well, grainy.  I used deinterlacing thinking that this would make a better video.

What can I do to get very high quality videos encoded to disc and should I be using deinterlacing?

Thanks

---

### Post by xc3RnbFO8P on 2009-01-31
Maybe you can find the answer about Deinterlace here:
[http://www.100fps.com/]("http://www.100fps.com/")

This grainy thing, you could repair it with less brightness and noise filter (in Avidemux, deiterlace doesn't).

---

### Post by umechanism on 2009-01-31
I tried using Avidemux but I can't seem to make it open .avi files.  I'm not very familiar with Avidemux to I'm not even sure if it will open .avi files in the first place.  Will it?

---

### Post by whaevr on 2009-01-31
I use avidemux a lot, I'm actually encoding a video right now..you should just have to drop the avi file in it and it should open it.

I have a lot of codecs installed also so that might be it?

If that doesn't work run avidemux through terminal 
```

avidemux2_gtk

```
and then drop the .avi file on it and see what happens.

---

### Post by umechanism on 2009-02-01
Ok.  I tried what you suggested but Avidemux still could not open it.  I did capture the text from the terminal window as Avidemux was running.  Does any of this reveal to you why Avidemux can not open the files?  By the way, I have to run Kino as root in order to get IEEE1394 to work correctly and all those imported files are "locked".  I even copied the files to a new location and reset the permissions to read/write.  Still can not open them.

```
michael@ubuntu-dell:~$ avidemux2_gtk
***************************
  Avidemux v2.4.3
***************************
 http://www.avidemux.org
 Code      : Mean, JSC, Gruntster 
 GFX       : Nestor Di , nestordi@augcyl.org
 Design    : Jakub Misak
 FreeBSD   : Anish Mistry, amistry@am-productions.biz
 Audio     : Mihail Zenkov
 MacOsX    : Kuisathaverat
 Win32     : Gruntster

Compiler: GCC 4.3.1
Build Target: Linux (x86)
User Interface: GTK+ (2.14.4)

Large file available: 1 offset

Initialising prefs
Directory /home/michael/.avidemux exists.Good.
Using /home/michael/.avidemux as base directory for prefs/jobs/...
Preferences found and loaded
[cpuCaps]Checking CPU capabilities
		MMX detected 
		MMXEXT detected 
		SSE detected 
		SSE2 detected 
		SSE3 detected 
		SSSE3 detected 
[cpuCaps]End of CPU capabilities check (cpuMask :ffffffff)

 Registering Encoders
*********************
MJPEG encoder registered
Xvid-4 encoder registered
FFmpeg encoder registered

3 encoder(s) registered

[SDL] Version: 1.2.12
[SDL] Initialisation succeeded
[SDL] Video Driver: x11


[Locale] setlocale en_US.UTF-8
[Locale] Textdomain was messages
[Locale] Textdomain is now avidemux
[Locale] Files for avidemux appear to be in /usr/share/locale
[Locale] Test: _File

Initializing Dithering tables
[xvid] Initializing global Xvid 4
[xvid] Build: xvid-1.1.2
[xvid] SIMD supported: (cf)
		MMX
		MMXEXT
		SSE
		SSE2

(avidemux2_gtk:8189): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Found 20 video encoder
Found 9 audio encoder
Found 13 Format 
Directory /home/michael/.avidemux/custom exists.Good.
No custom script
Found 0 custom scripts, adding them
Menu built
The screen seems to be 1920 x 1080 px
/dev/input/event0: Permission denied
/dev/input/event1: Permission denied
/dev/input/event2: Permission denied
/dev/input/event3: Permission denied
/dev/input/event4: Permission denied
/dev/input/event5: Permission denied
/dev/input/event6: Permission denied
/dev/input/event7: Permission denied
No physical Jog/Shuttle device found.
Initializing postproc
Deleting post proc
updating post proc
Enabled type:3 strength:3

 Registering Filters
*********************

Using real audio device
Spidermonkey initialized.
No crash file (/home/michael/.avidemux/crash.js)
46464952 -> 46464952
 
 Riff file detected... 
 AVI file detected...
** opening OpenDML files **
 Main avi header :
Indx found for track 0



```

---

### Post by punx45 on 2009-02-01
if the video is being put on DVD for general DVD player use, you should keep the interlacing.

also, i would avoid capturing the video in AVI.   it values size over quality.   that is probably part of the problem with your grainy picture.   capture in mpeg2 or DV first, (not familiar with the software so dont know what the choices are) then edit, then encode for intended media.

---

### Post by umechanism on 2009-02-01
I'll try that.  Thanks for the reply!

---

