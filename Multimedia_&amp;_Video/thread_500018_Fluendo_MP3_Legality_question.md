---
title: "Fluendo MP3 Legality question"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by blinx on 2007-07-13
Hello everyone.

My question is this:

Suppose I live in the US. Is it legal for me to use the (free) Fluendo MP3 codec on my ubuntu desktop?


(This is taken from the fluendo website [http://www.fluendo.com/resources/fluendo_mp3.php](http://www.fluendo.com/resources/fluendo_mp3.php))
> Issues to be aware of

If you are living in a country where the mp3 patents don't apply you can of course use the source code provided by Fluendo (or anyone else) to get legal mp3 support onto your Unix/GNU/Linux desktop.

On the other hand, if you live in a country where the patents apply, or if you are a distribution maker who sells your distribution in countries where the patents apply, then you need the licensed binary from Fluendo. This of course is no problem, but be aware that even if our binary is made from MIT licensed source code the resulting binary combined with our license is not free software, at least not GPL-compatible. This means that if you ship GStreamer with our binary mp3 plug-in, you need to be sure that you don't ship any GPL-licensed plug-ins that could end up being used together with the mp3 plug-in, as this would violate the GPL. And you don't want to violate the GPL. You also need to make sure you don't ship any GPL-licensed players which would use this plug-in.

Luckily most GStreamer plug-ins are LGPL and there are already playback applications out there with licensing terms that allow them to be used with non-free plug-ins. The Totem media player and the Banshee music player are two examples. 

This doesn't answer my question and they're forums are too complicated. So I ask here: Is it legal for me to use the fluendo mp3 plugin?

---

### Post by janbockaert on 2007-07-13
Yes it is legal. What they are talking about, is using the source code and building it in a program of your own (say you are programming a music player or a linux distribution). The fluendo plugin is free as in beer, but in in the us not free as in speech.

---

### Post by blinx on 2007-07-13
Thanks alot man. 

Just one more thing.. what about the gstreamer "ugly" codec packages?

Are they legal for me to use? 'Cause I noticed it says it has some license problems.. If yes, on any music player? If not, why does ubuntu provide them on the repositories?

---

