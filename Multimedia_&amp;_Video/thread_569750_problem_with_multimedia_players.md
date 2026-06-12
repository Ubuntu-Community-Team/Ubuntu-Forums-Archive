---
title: "problem with multimedia players"
date: 2007-10-07
forum: Multimedia &amp; Video
---

### Post by octotom on 2007-10-07
Whenever I try to play a file in totem or another multimedia player, it will start then disappear.  Nothing plays.  The only program I've gotten to work is banshee to play music.  How can I correct this?  

Tom

---

### Post by linuxwizard on 2007-10-07
Do you have all the codecs you need to play different formats installed ?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[https://help.ubuntu.com/community/Beginners/Guide/Feisty/Multimedia](https://help.ubuntu.com/community/Beginners/Guide/Feisty/Multimedia)

---

### Post by octotom on 2007-10-07
After typing in all the codes just to be sure, nothing has changed.  when I go to open up a video file or watch a dvd, Totem will just open up then close.  =(

---

### Post by britishbulldog on 2007-10-07
Try installing VLC, it has all the codecs for most of the popular file types. :guitar:

---

### Post by octotom on 2007-10-07
When I go to open music in VLC, it works, but when I try to open movies it just opens then closes.

---

### Post by linuxwizard on 2007-10-07
octotom
Have you tried other players ?
Here is a list of some different players you may want to try. Find one that works best for you. I like MPlayer the best IMO
[https://help.ubuntu.com/community/MultimediaApplications#framework](https://help.ubuntu.com/community/MultimediaApplications#framework)

---

### Post by octotom on 2007-10-07
I've been trying VLC and mplayer.  Each of them starts and then closes whenever I try to play a video.

---

### Post by RomeReactor on 2007-10-07
Hi. A very useful thing to do to diagnose a crashing application is to launch it from the command line; in Totem's case:
```
totem
```
If you have an Intel video card and the output in the terminal mentions a "BadAlloc" error, then it's a [known]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/109176") [bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/133726"). If you *do* get that, try the solution in [this reply]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/133726/comments/5") to the bug report.

---

### Post by octotom on 2007-10-07
I'm not sure what my video card is, but here is what the error says in terminal:

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 44 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


When I go to that bug page and try to put the stuff into xorg.conf, it says that the file is read only.  How do I change that so that I can add to it?

Tom

---

### Post by RomeReactor on 2007-10-08
To find out which video card you have, enter the following in the terminal:
```
sudo lshw -C display
```
and to modify your Xorg.conf file you need to open it in a text editor using administrator privileges (which means using sudo):
```
gksudo gedit /etc/X11/xorg.conf
```
**gksudo** is used for graphical applications; for command line programs, use **sudo**.

---

### Post by jfernyhough on 2007-10-08
This sounds to me like the xv issue with Intel graphics: are you running Compiz? On my machine if I run Compiz and try to watch a video the program will open and close as soon as it tries to play.

Try disabling Compiz (Desktop Effects) and playing the file again.

---

### Post by octotom on 2007-10-08
Disabling Desktop effects fixed it.  I'm glad that it was able to be fixed!  I noticed that it said on the Desktop effects window that it's experimental and blah blah.  In the future, will the program become compatible with intel graphics so that it won't be necessary to disable desktop effects when I want to watch a movie/video?

Thanks a bunch guys!
Tom

---

