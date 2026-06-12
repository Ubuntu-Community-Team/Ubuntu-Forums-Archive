---
title: "Ra,ram,asx files and radio stream"
date: 2007-09-25
forum: Multimedia &amp; Video
---

### Post by ili on 2007-09-25
Hi to all...after be able of play mp3 with amarok ,my next duty is to listen internet radio stations like the shows from the BBC in real audio and the Solid Steel show but this is in asx format ([http://www.ninjatune.net/solidsteel/playlist.php?play=1](http://www.ninjatune.net/solidsteel/playlist.php?play=1)) but when i do click over the link nothing happend,¿any ideas about this?
The rpm files opens on amarok but there is no audio and then amarok freezes:confused::confused: and i have to restart it!!!

And here is my final doubt:I have seen that exists file versions like gstreamer and xine but ¿are not both the same?,¿can i have it both at the same time?
I installed Amarok directly from the Add/Remove panel but i had read that it was just for kde , so i could installed it and run on gnome

Thanks

---

### Post by pay on 2007-09-25
Xine and gstreamer and api's for the mulimedia codecs, sort of like directshow on windows. Amarok can use either engine. Try ```
sudo aptitude install w32codecs gstreamer0.10-pitfdll
``` to get the real codecs.

---

### Post by ili on 2007-09-25
still the same, there is no audio :( i have the media player connectivity to play it on amarok but nothing

---

### Post by ili on 2007-09-26
do i have to install the real player???
i'm using the mediapalyerconnecivity from firefox...

---

### Post by ili on 2007-09-27
help

---

### Post by ili on 2007-09-28
if i install the real player could i sue the codecs to use it with amarok??

---

### Post by andrew.46 on 2007-10-02
Hi,

 Save the .asx files to your computer and open them with a text editor to extract the actual address of the stream; and then run with mplayer. For example:

```
$ mplayer mms://mercury.radica.com/festival2/current_streams/breaks/breaks_ninja_280907h.wma
```

works for me.

        Andrew

---

