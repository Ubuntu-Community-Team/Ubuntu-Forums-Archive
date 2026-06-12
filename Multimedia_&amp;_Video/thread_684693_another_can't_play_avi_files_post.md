---
title: "another can't play avi files post"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by chris23 on 2008-02-01
I've installed all  possible codecs that i found. I cant play avi file (divx/xvid) with neither player...
I was so desperated  that i tried automatix...but no luck...

any help guys?

---

### Post by Metaljaz on 2008-02-01
Try going to synaptic and doing a search for "totem-xine". Install it and uninstall totem-gstreamer. Or you can use the terminal and type:
sudo aptitude install totem-xine

Basically you are changing from GStreamer to Xine.
I couldn't get wmv files to play so I uninstalled totem gstreamer and installed totem xine. 
I also removed totem as my default audio player and switched to mplayer. i had to remove 2 symbolic links for totem by doing this from the terminal:
cd /usr/lib/firefox/plugins/
sudo rm libtotem-complex-plugin.so
sudo rm libtotem-complex-plugin.xpt

---

### Post by chris23 on 2008-02-04
Still no luck...
basically i want to uninstall all the codecs because i think there all messed up...
and make a clean install

---

### Post by stooshbunutu on 2008-02-04
Install VLC player

I have yet to find a media file extension it wont play. Very good and like everything Ubuntu... Its FREE!

Hope this helps :)

---

### Post by chris23 on 2008-02-04
I have it already installed but it can't play anything...

---

### Post by stooshbunutu on 2008-02-05
try converting it, assuming it isn't essential to have it as .avi format. I use [winff]("http://biggmatt.com/files/winff-0.33-i386.deb") that uses the [ffmpeg]("http://packages.ubuntu.com/gutsy/graphics/ffmpeg") codec to covert the file

hope this helps you, it works great for me.:)

ps what error messages are you getting from vlc?

Also you said you wanted to remove and re-install all the codecs, this can be done using synaptic manager.

---

### Post by thedaylights on 2008-02-08
I am having the same problem with Totem and VLC. VLC gives the message "unrecognized format". I thought I installed the restricted formats already, but maybe I did the wrong thing. How do I install restricted formats codecs?

---

### Post by Metaljaz on 2008-02-08
Try this wiki for the restricted formats:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by thedaylights on 2008-02-08
Thanks Metaljaz. Yeah I had in fact allowed those repositories so that's not the problem. I just finished following the massive [Complete Streaming, Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=661833"), to no avail. Still won't play .avi files. And streaming video is out for the BBC website, too.

---

### Post by Metaljaz on 2008-02-08
Try this site...maybe missed something (codecs section):

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Mplayer_with_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Mplayer_with_Multimedia_Codecs)

---

### Post by HappyFeet on 2008-02-08
> **thedaylights said:**
> Thanks Metaljaz. Yeah I had in fact allowed those repositories so that's not the problem. I just finished following the massive [Complete Streaming, Multimedia & Video How-to]("http://ubuntuforums.org/showthread.php?t=661833"), to no avail. Still won't play .avi files. And streaming video is out for the BBC website, too.

as far as streaming media, i found there's a conflict between totem and mplayer plugin. once i uninstalled totem (and its plugin) streaming media worked.

---

### Post by thedaylights on 2008-02-10
I went through the multimedia how-to again and I got mplayer working - it plays .avi files! For some reason Totem doesn't, but as long as I have one working player I'm happy.

---

