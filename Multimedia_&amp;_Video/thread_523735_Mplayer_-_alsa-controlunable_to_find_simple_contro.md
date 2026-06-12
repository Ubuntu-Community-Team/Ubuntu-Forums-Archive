---
title: "Mplayer - alsa-control:unable to find simple control 'PCM',0"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by signtist on 2007-08-12
Hello!

Mplayer has problems to play DVDs. works fine with xine, but when using mplayer I got the following message:

**-- Error opening/initializing the selected video_out**

I can start the dvd through the terminal with the following command:

**mplayer -vo x11 -vo xv -vo sdl dvd://**

but not through the GUI. I tried to edit the 

home/username/.mplayer/**gui.conf **

**vo_driver = "xmga**"

to

**vo_driver = "xv"** (or x11, or sdl etc)

when I do this the DVD starts but I get a stroboscope style error message (I mean Mplayer window - error message - Mplayer window, switching very fast between the two windows) after a while I managed to read the error message which says:

**alsa-control:unable to find simple control 'PCM',0 **

has anyone an idea?

many thanks!

---

### Post by ScottKidder on 2007-08-14
I'm having the same problem, after attempting to fix it, I lost sound completely somehow and did a fresh install, But, now I have the sound for the video, the PCM 0 error message still constantly flashes.

---

### Post by lippy on 2007-09-15
I had this problem too, which i solved, after searching for ages on the internet, by simply enabling "Enable Software Mixer" under the audio tab in Mplayer preferences.

---

### Post by banosd on 2008-02-07
Thanks, this worked for me.

---

