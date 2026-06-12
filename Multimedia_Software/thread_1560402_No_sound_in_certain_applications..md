---
title: "No sound in certain applications."
date: 2010-08-24
forum: Multimedia Software
---

### Post by MrRainMan on 2010-08-24
i've been googling this for the past hour to no answer.

Both rythmbox and Amarok refuse to play music and i get no error message. When I attempt to play an .mp3 file both media players speed up (i.e: finishing a 3min song in less then 5 seconds) and theres no sound...
This problem rosed after i installed "Docky" and the rhythmplayer control applet. 


**I do not have this problem when I play music (.mp3 or any other type of format) through VLC and "Movie Player"** (the media plays normally at the correct rate) 


What I've already ttried on my own:

- Restarting :(
- Reinstalling Rhythmbox and Amarok
- Tried reinstalling Gsteamer through the "Synaptic Package Manager"
- Uninstalled DOcky 

Nothing worked. 
-

---

### Post by MrRainMan on 2010-08-24
anyone? :(

---

### Post by MrRainMan on 2010-08-25
*sigh..*

well I guess ill reformat, [dw, this is the final bump]

---

### Post by tommcd on 2010-08-25
Since nobody else has offered anything better, try installing the **exaile** media player. It is much lighter and faster than Rhythmbox and Amarok; and it does pretty much everything you would want in a media player.

I don't know why you are having trouble with Rhythmbox and Amarok.
Have you installed the windows media codecs and the restricted formats:
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
See this about mp3 and Amarok:
[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)
That page references Ubuntu 6.06, which was quite a while ago. It is possible that the problem with gstreamer0.10-plugins-ugly still applies to Amarok though. Anyway, it is worth a try if you want to stay with Amarok. Personally I would recommend exaile.

---

### Post by orthopod on 2010-08-26
install  libxine1-ffmpeg library file  (i just searched for xine in synaptic)
completely remove and re install amaraok

and now amarok works for me

---

