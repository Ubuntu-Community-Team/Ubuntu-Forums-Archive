---
title: "Spectrum3d : software that shows the harmonics of the sound in 3D"
date: 2011-05-05
forum: Multimedia Software
---

### Post by victor-be on 2011-05-05
Hello to all

I'd like to introduce Spectrum3d, a new software that displays harmonics of the sound in 3D with OpenGL for Ubuntu

Audio source can be the microphone or an audio file, and it is Jack (jack-audio-connection-kit) compatible in option. Optionally, it can be run in real-time when not running with Jack; also optionally, it can receive multitouch input (either from touchscreen, or from touchpad).

X represents frequencies, Y represents amplitude of each frequencies and Z represents time. The perspective can be changed either by rotating or by translating the display around or along the 3 axis without limitations.

Here is a quick link to a demo video :  [http://www.youtube.com/watch?v=CCVxDNbcqRE]("http://www.youtube.com/watch?v=CCVxDNbcqRE")

It can be found here : [http://www.presences.org/download/spectrum3d-0.2.2.tar.bz2]("http://www.presences.org/download/spectrum3d-0.2.2.tar.bz2")

And here is a link to a tutorial explaining how it works : [http://www.presences.org/spectrum3d_tutorial_en.html]("http://www.presences.org/spectrum3d_tutorial_en.html")

It is free and under GPL licence. It uses the Gtk+, SDL, OpenGL, Gstreamer and uTouch-Geis free librairies. It works on Ubuntu 10.04, 10.10 and 11.04, but should work on other distributions also. Multitouch input however has not been tested on 10.04. It is still beta; testers are welcome. Thank you for your attention.

Victor

---

### Post by BicyclerBoy on 2011-05-06
What types of audio files will this program open/read ?
I'm guessing wav files..

Thx

---

### Post by victor-be on 2011-05-06
Hello and thank you for your interest

Since Spectrum3d uses Gstreamer, it can potentially read everything Gstreamer can handle, and this is huge; wav is supported as well as flac, ogg, mp3, mp4, wma, and ape ... among others;

However, if you want the last ones, be sure to install gstreamer-plugins-ugly and gstreamer-plugins-ugly-multiverse from repositories; install gstreamer-plugins-bad seems also necessary for proper functionning.

This is the advantage of using Gstreamer, that wants to be the most generic possible AFAIK, and hence allow to decode the largest choice of files

Victor

---

### Post by BicyclerBoy on 2011-05-06
"The Good, the Bad & the Ugly" has always been in my favourites..

Thanks..

---

