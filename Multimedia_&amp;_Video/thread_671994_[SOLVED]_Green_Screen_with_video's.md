---
title: "[SOLVED] Green Screen with video's"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by MojoMax on 2008-01-19
Whenever I try too play a video with VLC, MPlayer Kaffeine and Totem I get the sound but no video just a green screen i'm a newbie please help :(

---

### Post by lian1238 on 2008-01-19
Is it a plain green? Or messy green?
Does it happen with every video file? (i.e. Try playing ~/Examples/Experience ubuntu.ogg)
What type of file are you trying to play? (avi, mpg, wmv)?

Also, try running (Alt+F2) gstreamer-properties. Go to the video tab and Test the default output.

---

### Post by MojoMax on 2008-01-19
Its messy green with a few yellow lines. I've tried the exampe .ogg video and it works good in Totem. The file that i'm trying to play is an .avi file. I don't really understand what you mean by default output I got to he Video tab and pressed Test and its said that it didn't work or something :confused:

---

### Post by lian1238 on 2008-01-20
Do you have Xgl installed? If so, try uninstalled it. If not.. continue..

What was the error message when you tested the video?

Alto try: in VLC, go to Settings->Preferences. Expand 'Video', *click* on Output modules (under Video). Tick 'Advanced options' in the lower-right corner. Try all the options you have there. You need to restart VLC for the output module to take effect. (You may skip the ASCII's and image video output). Hopefully one of others will work. (X11?)

Edit: I have a similar (if not the same) problem. [**Link**](http://ubuntuforums.org/showthread.php?p=4128104)

---

### Post by MojoMax on 2008-01-22
It works now thanks a lot

---

### Post by DrMega on 2008-01-22
> **MojoMax said:**
> It works now thanks a lot

How did you fix it?

---

### Post by myle on 2008-01-31
I had the same problem and I solved by choosing:
Preferences > Video > Output Modules > Advanced Options > Videod output module > OpenGL video output

---

### Post by DaH-RaT on 2008-02-04
wow.. ok.. it worked :)

---

### Post by skychris on 2008-02-17
wow, it REALLY did work :):)

---

