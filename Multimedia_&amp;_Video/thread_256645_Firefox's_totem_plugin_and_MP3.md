---
title: "Firefox's totem plugin and MP3"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by magnusdeo on 2006-09-13
Hi 

I installed totem plugin for FF, becouse i want to listen to mp3, wma and other music files directly for browser. Plugin works; wma files works, but i have troubles with mp3. When i  want to hear one, firefox doesnt start plugin , but asking me where i want to download this mp3 file. 

How to configure thi plugin or firefox to play mp3 from sites?

Firefox about plugins looks like this: 

```

Totem Mozilla Plugin

    File name: libtotem_mozilla.so
    The Totem 1.4.3 plugin handles video and audio streams.


video/quicktime 	QT video 	mov 	Yes
application/x-mplayer2 	Plik wideo AVI 	avi, wma, wmv 	Yes
video/mpeg 	Plik wideo MPEG 	mpg, mpeg, mpe 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
video/divx 	Plik wideo AVI 	divx 	Yes
audio/wav 	Plik d&#378;wi&#281;kowy WAV 	wav 	Yes
```

---

### Post by Average Joe on 2006-09-17
Maybe you should install the:

gstreamer0.10-fluendo-mp3

package, if you haven't done so already. Without it, I don't think Totem can play mp3 files. I don't know much about the Firefox plugins though. I am having a hard time myself getting multimedia stuff to work with Totem.

Instead, I installed:

mplayer-386 and mozilla-mplayer

With that I can listen to mp3's on websites. No problems.

---

