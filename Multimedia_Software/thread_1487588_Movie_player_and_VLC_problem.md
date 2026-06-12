---
title: "Movie player and VLC problem"
date: 2010-05-19
forum: Multimedia Software
---

### Post by willix on 2010-05-19
Hy all,
I've got problems watching videos on an old DELL I'm trying to turn into a media center using the latest Ubuntu 10.4

Problem 1: Movie player shows a black screen
I've tried opening a couple of files (.avi, mp4) directly from the file browser but eventhough I hear the sound, I only get a **black screen**. When I actually click on a Movie player menu, I SEE the picture, but once the menu is released, the part displaying the menu stays black. However if I launch the movie player from the shell using the totem command, all is fine (I can watch my movie); but if I pass the name of the movie file, same black screen.
Anybody has an idea as to what's different when I open a totem with or without a file argument to play?


Problem 2: Movie player and VLC crashes:
I've had movie player and VLC crashing when opening other kind of files (.wmv, .mkv). I've tried running them from the command line and it looks like i haven't got enough resources

totem output
```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 73 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

vlc output
```
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  103
  Current serial number in output stream:  104
```

I do acknowledge that I only have 512MB of RAM however tracking my memory resources from the system monitor, it never goes over 50% . Furthermore, one of them is merly a Gigabyte, surly they DO NOT load ALL the file before playing it anyway, do they? 
Does somebody know a way round this?

---

### Post by willix on 2010-05-20
Well I've managed to solve the VLC problem:
open VLC player, goto Tools->Preferences->Video and select X11 for the display output and that prevents the crash :)

---

### Post by willix on 2010-05-21
Well following the instruction from [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) (part 1), I solved the other problems.
Funny how things work better when you read the instructions first ;-)

---

