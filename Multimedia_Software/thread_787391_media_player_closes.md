---
title: "media player closes"
date: 2008-05-08
forum: Multimedia Software
---

### Post by leah1984 on 2008-05-08
when i try to play a movie on either player totem or vlc the movie is there and all is good till i try to enlarge the screen or full screen it the entire window closes on me,i dont know why??:confused:

---

### Post by hermes0710 on 2008-05-09
Start these applications from a terminal (<alt>+F2 and type gnome-terminal.
In the terminal type the application name ex. "totem"). Then try enlarging the screen and since it crashes post the output of the console here to see what is going on.

---

### Post by leah1984 on 2008-05-19
i dont know what you mean? how do i start the app. from the terminal ,do i type alt f2 in the terminal? could you explain a little easier for a noob? i know how to get the terminal open i tryed hitting alt F2 and nothing happened.

---

### Post by leah1984 on 2008-05-19
how do i know what my gnome terminal is?

---

### Post by leah1984 on 2008-05-19
well i tryed a few things and something came upit said bash command not found due to
 unexpected token

---

### Post by sidney_jec on 2008-06-10
this is the error message i get when it starts the search for codecs..

siddhartha@siddhartha-desktop:~$ totem
** Message: don't know how to handle video/x-xvid, framerate=(fraction)25/1, width=(int)480, height=(int)368
** Message: don't know how to handle audio/mpeg, mpegversion=(int)1, layer=(int)3, rate=(int)48000, channels=(int)2, codec_data=(buffer)0100000000004f0101000000
** Message: Error: You do not have a decoder installed to handle this file. You might need to install the necessary plugins.
gstplaybasebin.c(2284): prepare_output (): /play

** Message: Missing plugin: gstreamer|0.10|totem|MPEG-1 Layer 3 (MP3) decoder|decoder-audio/mpeg, mpegversion=(int)1, layer=(int)3 (MPEG-1 Layer 3 (MP3) decoder)
** Message: Missing plugin: gstreamer|0.10|totem|XVID MPEG-4 decoder|decoder-video/x-xvid (XVID MPEG-4 decoder)

** (gnome-codec-install:6088 ): WARNING **: return value of custom widget handler was not a GtkWidget
** Message: Missing plugin installation failed: installer-exit-unclean

---

