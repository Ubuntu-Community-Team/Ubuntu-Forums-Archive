---
title: "Managing iPod with ALAC!"
date: 2015-10-22
forum: Multimedia Software
---

### Post by garrie2 on 2015-10-22
Hi there,

I want a piece of software that allows me to manage my iPod (classic, latest generation) that allows me to transfer M4A/ALAC files. 

I'm almost 100% sure I've used Rhythmbox to do this in the past, but it seems now that Rhythmbox always converts to mp3 everytime I try to load ALACs onto the iPod. There doesn't even seem to be an option to control the quality of the MP3 that it gets converted to - nonsense, really.

Anyway, is there a way to fix Rhythmbox so it transfers ALAC, and if not, is there an alternative software that will do it?

---

### Post by shantiq on 2015-10-22
[FONT=arial]hi garrie have you looked at [clementine]("https://www.clementine-player.org")

i seem to remember it also requires [COLOR=#111111]gstreamer0.10-plugins-bad  to be installed to play/process alac

install:
[/COLOR]
```
[/FONT][FONT=arial]sudo add-apt-repository ppa:me-davidsansome/clementine
[/FONT][FONT=arial]sudo apt-get update ; sudo apt-get install clementine [/FONT][COLOR=#111111][FONT=arial]gstreamer0.10-plugins-bad[/FONT][/COLOR][FONT=arial][COLOR=#111111]
[/COLOR]
```[/FONT]

---

### Post by Yellow Pasque on 2015-10-22
I think you need gstreamer0.10-ffmpeg and gstreamer1.0-libav for ALAC support in Clementine and Rhythmbox, respectively. Whether that allows you to put an ALAC on the ipod or not, I don't know.
```
$ gst-inspect-1.0 | grep -i alac
libav:  avdec_alac: libav ALAC (Apple Lossless Audio Codec) decoder
libav:  avenc_alac: libav ALAC (Apple Lossless Audio Codec) encoder
$ gst-inspect-0.10 | grep -i alac
ffmpeg:  ffdec_alac: FFmpeg ALAC (Apple Lossless Audio Codec) decoder
ffmpeg:  ffenc_alac: FFmpeg ALAC (Apple Lossless Audio Codec) encoder
```

> There doesn't even seem to be an option to control the quality of the MP3 that it gets converted to - nonsense, really.
I ran into this on another Gnome app (it may have been sound-juicer). Gnome devs got over-zealous with their "remove options so we don't confuse the user" theory.

---

### Post by andrew.46 on 2015-10-27
I also have an iPOD classic, the last release :). I convert to alac with the latest abcde and then transfer with gtkpod. Perhaps try this?

---

