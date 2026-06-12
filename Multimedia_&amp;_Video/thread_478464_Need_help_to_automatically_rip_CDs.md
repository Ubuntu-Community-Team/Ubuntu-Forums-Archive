---
title: "Need help to automatically rip CDs"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by bogoliubov on 2007-06-19
Hello. I'd like to rip all my CD collection to MP3. I'd prefer OGG/FLAC, but my portable player can only play MP3s. 
Since I have around 300 discs I'd like it to be automatic so that I put in a CD and then it's automatically ripped (with the correct song-names etc) to the harddrive and then the disc is ejected so I can put in the next and so on.

Is there any way to do this in Ubuntu? I know my way around simple bash-scripts, but apart from that I have no programming skills.

---

### Post by bogoliubov on 2007-06-19
I found a nice flag in sound-juicer that did this. So I guess it's solved...

On the other hand, ripping is really slow; I have no idea why...?!

---

### Post by kexodusc on 2007-06-22
> **bogoliubov said:**
> I found a nice flag in sound-juicer that did this. So I guess it's solved...

On the other hand, ripping is really slow; I have no idea why...?!

I think (and someone correct me if I'm wrong) that the default ripping program in Sound Juicer is cdparanoia, which likes to get a good read on the disc to ensure quality.  This link shows you how to change the gstreamer pipeline to speed up ripping.

[http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/presets.html](http://lame.cvs.sourceforge.net/*checkout*/lame/lame/doc/html/presets.html)

---

### Post by Major_Kong on 2007-06-22
> **bogoliubov said:**
> I found a nice flag in sound-juicer that did this. So I guess it's solved...

On the other hand, ripping is really slow; I have no idea why...?!

How long does it take on avg. ?


PS: If your mp3 player supports VBR, it's a good idea to change the encoding settings to MP3 VBR.

e.g.:
audio/x-raw-int,rate=44100,channels=2 ! lame quality=0 vbr=4 vbr-quality=5 ! xingmux ! id3v2mux

(encodes to a near transparent (transparent = most people cannot distinguish the mp3 from the original in an ABX blindtest) ~130 kbps MP3 VBR.
If you do change the gstreamer pipeline use gconf-editor (system>gstreamer>0.10>audio>profiles) not sound-juicer to change the profile.

[http://www.hydrogenaudio.org/forums/index.php?showtopic=28124](http://www.hydrogenaudio.org/forums/index.php?showtopic=28124) - More info.

---

