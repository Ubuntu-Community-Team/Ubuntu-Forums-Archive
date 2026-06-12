---
title: "[HELP] Mencoder Resize = No Subtitle"
date: 2010-06-24
forum: Multimedia Software
---

### Post by randall87 on 2010-06-24
Hi all,

I hope someone can really help me here as I have been stuck for weeks and still can't find the solution with google. :(

The subtitle for the video won't be display whenever I use the the command [COLOR=Red]**"-vf scale"**[/COLOR] to resize the video. 

**Able to display subtitle but [COLOR=Magenta]no resize[/COLOR]:**

[mencoder]("http://www.videohelp.com/tools/MPlayer") test/22.avi -o test/22.flv -of lavf -oac mp3lame -lameopts abr:br=56 -ovc lavc -lavcopts vcodec=flv:vbitrate=1000:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -srate 22050 -ofps 24 [COLOR=DarkGreen]-sub test/subtitle.srt -subpos 90 -subfont-text-scale 3.5[/COLOR]

**Unable to display subtitle but [COLOR=Magenta]resizing works[/COLOR]:**

[mencoder]("http://www.videohelp.com/tools/MPlayer") test/22.avi -o test/22.flv -of lavf -oac mp3lame -lameopts  abr:br=56 -ovc lavc -lavcopts  vcodec=flv:vbitrate=1000:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -srate  22050 -ofps 24 [COLOR=Red]**-vf scale=320:240**[/COLOR] [COLOR=DarkGreen]-sub test/subtitle.srt -subpos 90  -subfont-text-scale 3.5[/COLOR]

---

