---
title: "Xubuntu Jaunty Jackalope - video doesn't play any more"
date: 2009-04-28
forum: Multimedia Software
---

### Post by bravo sierra echo on 2009-04-28
Hello,

Since upgrading to Jaunty Jackalope, video no longer works - any video format (.avi, .mpeg etc), DVDs and even embedded video in sites like YouTube (I get the audio on YouTube but no video).

The video player (VLC or Totem) loads then immediately quits.

Under Hardy Heron and Intrepid Ibex I went through the usual instructions for enabling DVD and installing the codecs etc but that doesn't help this time.

Release 9.04 (Jaunty)
Kernel Linux 2.6.28-11-generic
GNOME 2.26.1

Can anyone help?

---

### Post by x33a on 2009-04-28
take a look here

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-904-jaunty.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-904-jaunty.html)

---

### Post by bravo sierra echo on 2009-04-28
Thank you but still no joy :(

Mplayer quits out in exactly the same way, just giving me enough time to read the error message "Could not connect to server" or something like that!

---

### Post by x33a on 2009-04-28
in vlc and mplayer, try different video output modules(before opening a file), and see if the crash occurs with all output modules.

---

### Post by bravo sierra echo on 2009-04-29
Having a slow day and can't spot those in the preferences...  where should I be looking please?

---

### Post by x33a on 2009-04-29
in mplayer: open preferences, click on video tab -> available video drivers, try x11, gl, gl2, and see if the crash occurs with all three.

in vlc, open preferences -> click on video on the left. 
look for output -> change it to opengl or x11.

---

### Post by amast on 2009-05-01
I'm having the same problem, both with an upgrade to Jaunty and also with a fresh installation.  Now, I noticed the screen flashed when I loaded a video & DVD to play.  I wonder if this is related to my using dual monitors or my Intel 945 video driver?  It would appear they added newer and better video card support with Jaunty because I got dual monitor support right out of the box which was awesome!  

I'm sad... Well, youtube works fine for me.   But the only application I can get any response on a DVD from is acidrip preview and with that I only get audio.  Something is very wrong here.  

Who ISNT having this problem and using dual monitors?

---

### Post by x33a on 2009-05-01
hi amast,

please create a new thread for your problem, as it is a bit different than this one and you'll get better support too.

---

