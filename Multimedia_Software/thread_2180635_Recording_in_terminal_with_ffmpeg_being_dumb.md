---
title: "Recording in terminal with ffmpeg being dumb"
date: 2013-10-14
forum: Multimedia Software
---

### Post by josh17 on 2013-10-14
I tried recording some games with ffmpeg in terminal, the game runs great but when i play the video its laggy as crap and completely stops showing any movement half way through, whats going on??? ><

This is the code i type to record: ```
ffmpeg -f x11grab -s 720x640 -r 24 -i :0.0+645,52 -sameq /home/josh/Desktop/video.mpg
```

---

### Post by shantiq on 2013-10-14
hi Josh    try this ffmpeg or avconv


> GRAB DESKTOP FFMPEG or AVCONV   use either
=================== ===============
sound


avconv -f alsa -ac 2 -i pulse -f x11grab -r 30 -s [COLOR=#000000][FONT=Ubuntu Mono]720x640[/FONT][/COLOR] -i :0.0 -acodec flac  -y -threads 0 -b:v 5000k ./Desktop/mydesktop.mkv




image only


avconv   -f x11grab -r 30 -s [COLOR=#000000][FONT=Ubuntu Mono]720x640[/FONT][/COLOR] -i :0.0   -y -threads 0 -b:v 5000k  ./Desktop/mydesktop.mkv


---

### Post by josh17 on 2013-10-14
> **shantiq said:**
> hi Josh    try this ffmpeg or avconv

That runs great! but the quality isn't very good, is there a way to make the quality just a tiny bit better?

---

### Post by shantiq on 2013-10-14
is [COLOR=#000000][COLOR=#000000]*[FONT=Ubuntu Mono]720x640[/FONT]*[/COLOR][/COLOR][COLOR=#000000]*    really the size of your screen    i use 1600x900 here    but maybe your screen is really *[/COLOR][COLOR=#000000][COLOR=#000000]*[FONT=Ubuntu Mono]720x640[/FONT]*[/COLOR][/COLOR][COLOR=#000000][I] 

so to bump up the kbps on the video should increase the quality of the image A LOT


[/I][/COLOR]```
[COLOR=#000000]*avconv -f x11grab -r 30 -s *[/COLOR][COLOR=#000000][COLOR=#000000]*[FONT=Ubuntu Mono]720x640[/FONT]*[/COLOR][/COLOR][COLOR=#000000]* -i :0.0   *[/COLOR][COLOR=#000000]*-y -threads 0    *[/COLOR][COLOR=#800000]*-b:v 5000k*[/COLOR][COLOR=#000000]*   ./Desktop/mydesktop.mkv*[/COLOR]
```   or

```
[COLOR=#000000]*ffmpeg -f x11grab -r 30 -s *[/COLOR][COLOR=#000000][COLOR=#000000]*[FONT=Ubuntu Mono]720x640[/FONT]*[/COLOR][/COLOR][COLOR=#000000]* -i :0.0   *[/COLOR][COLOR=#000000]*-y -threads 0    *[/COLOR][COLOR=#800000]*-b:v 5000k*[/COLOR][COLOR=#000000]*   ./Desktop/mydesktop.mkv*[/COLOR]
```

or go even higher say 7000k  or even 9000k if your machine can hack it;   mine struggles with 9000  ::]]
even 2500 gives you good quality   ,,,,    i forgot the default but it is ridiculously low hence what you saw

anyway play with the kbps see what you get ...

---

### Post by FakeOutdoorsman on 2013-10-14
See [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

---

