---
title: "new webcam, no driver. what do i do? (samsung pleomax pwc-2000)"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by theheadlessrabbit on 2007-12-24
I just bought a Pleomax pwc-2000 USB webcam  (its from samsung)

and it doesn't work. 

camera monitor, skype, cheese, camorama, and ekiga won't detect any webcam at all.
i keep getting a "could not connect to video device (/dev/video0) please check connection" error message.


easycam give me 6 options, each one generates outputs like this:

"Forum address : [http://forum.ubuntu-fr.org/viewtopic.php?id=16670](http://forum.ubuntu-fr.org/viewtopic.php?id=16670)
Email address : [email]jbtheou@gmail.com[/email] 
Please forward me the following text to one of following addresses :  
ID 093a:2600 Pixart Imaging, Inc."

I've read though lots of other webcam threads, and none of them seem to work.

I also tried this, with no luck:
> 
kyle@kyle-laptop:~$ mplayer tv:// -tv driver=v4l:width=640:height=480:device=/dev/video0
MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Mobile AMD Sempron(tm) Processor 3200+ (Family: 15, Model: 76, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l
 name: Video 4 Linux input
 author: Alex Beregszaszi
 comment: under development
unable to open '/dev/video0': No such file or directory


MPlayer interrupted by signal 11 in module: demux_open
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
kyle@kyle-laptop:~$ 



i doubt it means anything, but the little LED does turn on when i plug it in, but that all that happens. 


I would really like to get this thing working, I hate having to restart my system and booting in winXP every time i want to use my webcam.

any help would be great.

and merry Christmas!

---

### Post by hellfire_bg on 2007-12-28
Did you get your webcam working? I have the same webcam (Bus 003 Device 002: ID 093a:2600 Pixart Imaging, Inc.) and it does not work for me. I`ve been searching through various forums and google for an hour already and still i can`t find nothing of help.


EDIT
I managed to get this webcam working in debian with the gspca drivers. The steps i did to install the driver are as follows:
apt-get install gspca-source
m-a prepare
m-a a-i gspca
After that the webcam should work. If the module does not autoload put it in /etc/modules. I still have some problems though. The color of the video is strange - it has colors but it is almost black and white and the quality of the picture is low. This may be just how the camera is though - i think it is a low end webcam.

---

