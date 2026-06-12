---
title: "VLC displays subtitles selectively?"
date: 2008-07-03
forum: Multimedia Software
---

### Post by aethralis on 2008-07-03
With VLC media player 0.8.6e Janus (wxWidgets interface) I have on the second screen (xvideo alternate fullscreen method, screen 1) only _some_ of the subtitles shown (but they are present in the srt file). It means that some lines display correctly but some just are not displayed. Tried and deleted the .vlc/ folder (that sometimes helps) but no avail. The problem persists. Any ideas?? I might add that totem-gstreamer displays those subtitles without problems (I would use totem, but that is not able to crop widescreen video, or so it seems).

---

### Post by cowkiller on 2008-07-24
I was having this very same problem up to yesterday, but surprisingly today everything worked fine, just by itself. I think I didn't do anything to solve this problem so I'm afraid that it will come back at any time. 
If someone could throw some light on this it would be great, because it's a really annoying problem that I've been draggin behind since my first experience with ubuntu, and never could find any useful info.

---

### Post by XxsydenxX on 2008-07-24
Actually, this mostly happens in mkv files the best thing to do about this is use xine, or mplayer. Vlc is only good on windows in my opinion

---

### Post by cholguin on 2008-08-20
I found a solution, actually is pretty simple. When ever you want to load a movie with its substitles, instead of just clicking the movie, just open the VLC, go to "File> Open File", and in the space for "Open" Browse your movie and select it, then mark "Use a Subtitle file" and in the space for "File" Browse your subtitle file, then click on "Advance Settings" and in the Subtitles text encoding drop down menu choose ISO-8859-1 (This is a standard character encoding of the Latin alphabet, if your subtitles are in another language check for your encoding) click OK on the window, click OK again and your movie should load with your subtitles. 

Remember ISO-8859-1 is only for latin languages, check if your language is part of the coverage in this page: [http://en.wikipedia.org/wiki/ISO-8859-1#ISO-8859-1](http://en.wikipedia.org/wiki/ISO-8859-1#ISO-8859-1), if not check for your correct encoding.

This did it for me.

God bless and enjoy your movies :popcorn:

---

### Post by dorukaelp on 2008-11-11
it works quiet well, i had the same problem as well. thanks

---

