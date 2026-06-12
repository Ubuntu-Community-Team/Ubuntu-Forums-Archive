---
title: "Can not play wmv file"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by snowstorm on 2007-04-27
Trying to play wmv files in feisty with kaffeine but it only shows a black screen. 

I did add medibuntu to my sources.list and installed the restrictive formats with adept installer in the "other" category. I also installed the w32codecs from medibuntu. But now I ran out of ideas. Any more suggestions on what packages or library files I need to install?

---

### Post by madmetal on 2007-04-27
> **snowstorm said:**
> Trying to play wmv files in feisty with kaffeine but it only shows a black screen. 

I did add medibuntu to my sources.list and installed the restrictive formats with adept installer in the "other" category. I also installed the w32codecs from medibuntu. But now I ran out of ideas. Any more suggestions on what packages or library files I need to install?

there is only a .wmv file you cant open or every .wmv ?
give a try with VLC player..

---

### Post by snowstorm on 2007-04-27
It's with every wmv file I tried. I tried one here [http://www.amd.com/it-it/Corporate/VirtualPressRoom/0,,51_104_572_585,00.html](http://www.amd.com/it-it/Corporate/VirtualPressRoom/0,,51_104_572_585,00.html), after googling with file:wmv as search terms and it also gives me a black screen. With vlc the program just crashes, no error message.

---

### Post by norton1 on 2007-04-27
try opening two instances of kaffine or vlc and see if that works - if it does it's a weird bug i had too in edgy - i got round it by installing windows media player in crossover office - but i think there are other wys around it

---

### Post by ubu-for on 2007-04-27
> **snowstorm said:**
> It's with every wmv file I tried. I tried one here [http://www.amd.com/it-it/Corporate/VirtualPressRoom/0,,51_104_572_585,00.html](http://www.amd.com/it-it/Corporate/VirtualPressRoom/0,,51_104_572_585,00.html), after googling with file:wmv as search terms and it also gives me a black screen. With vlc the program just crashes, no error message.

VLC, MPlayer and Totem-Xine work great!

---

### Post by visible on 2007-04-27
[http://ubuntuforums.org/showthread.php?t=413626]("http://ubuntuforums.org/showthread.php?t=413626")
have you followed this how to?  this is the one I followed and everything is working fine for me.
the only snag I ran into was I had to install the w32 and libdvdcss pakages through synaptic.  the downlowds kept failing in terminal.

---

### Post by snowstorm on 2007-04-27
Apart from the gstreamer stuff (I use kubuntu) everything is installed from that link, such as:

- libdvdcss2
- w32codecs
- medibuntu (this upgrades amarok, k3b etc)
- macromedia flash plugin (although irrlevant in this case)

I also installed things like:
- ffmpeg and libxine1-ffmpeg
- libxine1
- amarok-xine
- kaffeine-xine
- libxine1-kde
- libxine-extracodecs

well, I don't know what else could be relevant, but if somebody tells me I'll check it out

---

### Post by snowstorm on 2007-04-27
> **norton1 said:**
> try opening two instances of kaffine or vlc and see if that works - if it does it's a weird bug i had too in edgy - i got round it by installing windows media player in crossover office - but i think there are other wys around it

I can not open two instances of kaffeine. On edgy I had no problems with video files. But I don't wanna go back. :-)

---

