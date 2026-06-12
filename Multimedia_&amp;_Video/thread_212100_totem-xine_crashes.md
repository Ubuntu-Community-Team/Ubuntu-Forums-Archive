---
title: "totem-xine crashes"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by mommebu on 2006-07-09
Till today totem worked just well on my toshiba a100-206, but after i installed ffmpeg and sox today, it crashes on launching from the menu or from command line with or without argument.
The behaviour matches descriptions of other users:
- if I use totem-gstreamer instead of totem-xine it works
- after I installed xine-ui, when i start xine (the x-ui) first and then totem-xine it works fine
- without xine started it keeps crashing
- reintstallation of the directly involved files didn't help

as mentioned above this behaviour was already observed by others without any real solution to the problem, just that in my case e.thing worked fine till I did this extra installations today, so I suppose that a reinstalltaion of the right package could help?

anybody any idea?

cheers.

---

### Post by woedend on 2006-07-09
can you run totem from a terminal and catch error messages?

---

### Post by mommebu on 2006-07-09
here is the error message:
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 92 error_code 2 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

i fear it's not to yielding too much information though...

---

### Post by mommebu on 2006-07-09
in the meanwhile I found out:
-reducing the start-up logo totem_logo.png in size, as suggested by other users didn't help.
-deleting totem_logo.png and creating an empty file with 'touch totem_logo.png' resolved the crash problem, apart from the fact that it leaves the image area messed up playing sound files.

---

### Post by Phenz on 2006-07-17
I'm getting the same exact error when trying to run totem from the main menu.  I later put in a dvd and found that totem auto-ran with xine, but still wont run when launched normally.:( 

ErrorDetails: serial 92 error_code 2 request_code 141 minor_code 19

---

### Post by H.E. Pennypacker on 2006-07-22
I too am getting this problem, and when starting Totem through the terminal, I get the following error, which is similar to what the original poster posted:

The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 86 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I should probably report this on the launch-pad, as well as file a report with Gnome (their website).

> **mommebu said:**
> in the meanwhile I found out:
-reducing the start-up logo totem_logo.png in size, as suggested by other users didn't help.
-deleting totem_logo.png and creating an empty file with 'touch totem_logo.png' resolved the crash problem, apart from the fact that it leaves the image area messed up playing sound files.

How did that solve the problem?

---

### Post by H.E. Pennypacker on 2006-07-22
I have solved this problem by following this bug report:

[https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229](https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229)

---

### Post by adds2one on 2006-08-28
H. E. Pennypacker what exactly did you do to solve your problem. By looking at your error output it seems you have a different problem from that documented in your link.

I get the same error as you. The only thing that totem-xine, (or mplayer or VLC) won't play for me is DVDs. The app will open for a second asnd then close giving the error you posted.

All the people in the bug report link are having problems with totem playing files when they open totem first(rather than just clicking a file)

Please let me know what your fix was.

Thank you.

---

### Post by mommebu on 2006-08-29
for me the problem was solved with the last totem-xine update to version 1.4.3...
Sounds to me that you have a different problem though as not even mlplayer and others work to play DVDs. Maybe some Codec is missing, strange that it crashes though.
What message does mplayer give you when you try to play a DVD?

---

### Post by adds2one on 2006-08-30
how do I get totem to run as totem-gstreamer to run so I can see if this helps me or not?

---

### Post by mommebu on 2006-08-31
installl totem-gstreamer from the package manager.
this should remove totem-xine automatically.

---

### Post by adds2one on 2006-08-31
OK, I tried totem-gstreamer but to no avail.

I have all the codecs installed and totem-gstreamer keeps telling me that I don't have the right plugins installed. A quick search on the forum reveals a lot of people with this same "no plugins" issue and as yet no solution.

It seems that it may be impossible for me to play DVDs in Ubuntu. I have tried totem-gstreamer, totem-xine, mplayer, ogle and VLC media player. I have all the codecs and restricted format support installed through Automatix as well as seperately installed W32codecs. I am using an ATI Rage 128 video card which has played DVDs perfectly for years when this machine was a Windows XP box. I have no problem playing any other kind of video, only DVDs will not play.

Is there really nothing else I can do to get DVDs to play in Ubuntu?

---

### Post by mommebu on 2006-09-01
another try could be xine itself (not totem-xine), I remember reading that for some people it seemed more stable...

---

