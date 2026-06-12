---
title: "Problem with mkv files players crash"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by Freiburg05 on 2007-05-07
After upgrading to 7.04 I'm having some trouble to play mkv files. All of my players (totem-xine, mplayer, vlc)crash when I try to open a mkv file. So far all other multimedia files work fine. The next is the error I get with totem:
[I]
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 637 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/I]

in vlc:
[I]
   VLC media player 0.8.6 Janus
[00000547] skins2 interface: skin: VLC 0.8.5 Default Skin  author: aLtgLasS
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84
[/I]

     I've read other posts about similar issues. I have no ATI or Nvidia graphic card, mine is an integrated Intel 82852/855GM card. I've tried switch the video output to X11, as suggested in one thread, and I got it to work in vlc and mplayer. However, in vlc the plays very slow and the image jumps often. In mplayer, image and sound go out of sync.


      I suppose I have to wait for a solution a bit longer, but if anybody knows a workaround I would be happy to try it. Any Ideas are welcome.

     Bye!

---

### Post by Freiburg05 on 2007-05-08
Hy there!

    No one has any ideas... 
        Am I the only one with this problem? or is it already solved somewhere in forums?

---

### Post by LucanUK on 2007-05-17
Hey...

Same problem, but not from an upgrade. I also have an intel GFX chipset...

Was there a solution or have I missed something in the forums?

Cheers

Lucan

---

### Post by kef1 on 2007-09-03
Hey there.

I was having the same problems as you two until I installed the drivers for my Intel Graphics Processor (Intel 845GV to be exact). Now it works like a charm. Hope that helps.

[http://ubuntuforums.org/showthread.php?t=434175]("http://ubuntuforums.org/showthread.php?t=434175")

---

