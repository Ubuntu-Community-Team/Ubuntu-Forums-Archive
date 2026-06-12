---
title: "stage6 videos not working in firefox--done everything--nothing works."
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by spandanj on 2008-01-26
OK,

so I have READ almost ALL THREADS on installing mplayer for firefox...ALL!

and, nothing seems to work. Here is my story:

                  Firefox seem to play joox.net and stage6 divx files alright. but, suddenly it stopped. dont know why. so, the streaming area would just remain gray, it would say connecting, then connected, then sometimes buffering, and sometimes playing. but NOT ever actually playing, even when i did right click-->play. and in the end it would be "stopped". also, sometimes, firefox would crash trying to play the divx file.

so, i unstalled all plugins, uninstalled firefox, --> reinstalled everything. STILL, it doesn't work. so, then i installed media connectivity plugin - not helpful...


I am DESPERATE. can somebody please help me!!??? thank u

---

### Post by Sqwishy on 2008-01-26
Possibly try using totem-xine instead of totem-gstreamer, install the totem-xine package by running the command "sudo apt-get install totem-xine" (without the quotes) in your terminal. You might need to install some extra libraries... but i doubt it. I don't know what they're called off the top of my head, i think it's libxine1-something...

---

### Post by whazooo on 2008-01-26
Right click the stage 6 movie area in your browser, then click about
What does it say?

As was stated by sqwishy
The totem xine plugin is the way to go.

---

### Post by eye208 on 2008-01-26
> **whazooo said:**
> The totem xine plugin is the way to go.
Stage 6 works fine with default Totem GStreamer too.

Of course you need to install some GStreamer codecs first. I've outlined the procedure [here](http://ubuntuforums.org/showthread.php?p=4209633#post4209633).

---

### Post by spandanj on 2008-01-26
ALMOST there....


ok, so i removed mozilla-mplayer plugin. thus, now the joox divx files start in gstreamer. as you told me to do i right clicked and open in gstreamer. it did. Great. and it started buffering. HOWEVER, it would buffer every few seconds...very annoying...

is there a way to make it buffer better or buffer more before it plays?

AND, why is there so much hype about mozilla-mplayer plugin...when the default gstreamer works? 

- THANK you so much for your help

---

