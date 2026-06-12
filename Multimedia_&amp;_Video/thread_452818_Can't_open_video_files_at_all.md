---
title: "Can't open video files at all"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by Repsa_Jih on 2007-05-23
When I try to open a video file (.mpg), either using totem-gstreamer, totem-xine, or vlc, the program quits directly. I am quite sure I have the correct plugins and codecs though...

---

### Post by sygin on 2007-05-23
Hi Repsa_Jih,

You should always get an error message/dialogue even if you do not have the correct codec. It would seem that there is a issue that is affecting all video playing applications. To help solve this problem:

1. What Ubuntu Linux are you using?

2. What video card are you using?

3. Run a player from a terminal window and post the error messages here.

If you could answer all or any of the above questions it would be helpful.

To run totem from a terminal window:
1. Open at terminal window (one of the menu options does this, in KDE it is under System and is called Konsole)
2. type: 

totem 

and then press enter.

All the best,
Sygin

---

### Post by Repsa_Jih on 2007-05-23
1. Ubuntu Linux 7.04, Fiesty Fawn

2. Intel accelerated graphics

3.

jasper@jasper-laptop:~$ totem
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 44 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by Flump5000 on 2007-05-23
use automatix and download all the codecs. that should make it play dvds and other stuff you willl need to do in the future. im new too. i just figured it out today.

---

### Post by Repsa_Jih on 2007-05-23
Never mind, I fixed it.

The solution was to disable compiz...

---

### Post by stchman on 2007-05-23
> **Repsa_Jih said:**
> When I try to open a video file (.mpg), either using totem-gstreamer, totem-xine, or vlc, the program quits directly. I am quite sure I have the correct plugins and codecs though...

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse

These are the codecs you will need to play music and video.

---

### Post by satx on 2007-05-23
Download Mplayer! Works like a champ in Firefox and for any website. Go to Applications, Add/remove, Show all available applications, and select Sound and Video, or just search for Mplayer.

SATX says this!

---

### Post by Dave Crowhurst on 2007-09-01
Yep, I had the same problem. Tried to play a .mpg file and VLC just quit. 

I disabled desktop effects and now it plays okay.

---

