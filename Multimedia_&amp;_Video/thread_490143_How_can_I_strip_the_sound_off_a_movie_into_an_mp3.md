---
title: "How can I strip the sound off a movie into an mp3?"
date: 2007-07-02
forum: Multimedia &amp; Video
---

### Post by CheeseEatingBulldog on 2007-07-02
I just downloaded some Glastonbury vids of the net and would like to strip the music to mp3 so I can listen to it on my ipod. Does anyone know how to do this?

---

### Post by lisati on 2007-07-02
I've used Windoze software to do this job but don't know that any that would work with Linux,,,,

Anyone?

---

### Post by RomeReactor on 2007-07-02
Hi. In what format is the movie (DVD, avi, mpg, etc)? I think [AviDemux]("http://en.wikipedia.org/wiki/Avidemux") could help (though I don't think it works with DVDs). You can find AviDemux through Add/Remove, Synaptic, or from the terminal:
```
sudo apt-get install avidemux
```

---

### Post by CheeseEatingBulldog on 2007-07-02
It's just an .avi file of the Arctic Monkeys :) and wanted to strip it to mp3.

---

### Post by aquavitae on 2007-07-02
You can use mplayer.  You can do it with the gui, but I'm not sure how - I usually use the command line:
mplayer movie.avi -ao pcm:file=audio_output.pcm -vo null
This will send the audio to the file audio_output.pcm and won't display the video.  You can then use lame (make sure you have lame installed) to encode it to mp3:
lame audio_output.pcm audio_output.mp3

There's probably a graphical tool to do this, but I fin'd it easier on the command line so I've never bothered to look.  Btw, another useful program is audacity which can edit mp3s.

---

### Post by CheeseEatingBulldog on 2007-07-02
Thanks for the advice, am now using avidemux which seems to be encoding to lame from avi, if that doesn't work I will do the command line option, not afraid of CLI, so good to have a plan-B. And thanks for mentioning the editing, that will be usefull if I get a file out of it and need to split the tracks.

--edit---
It produced a non labeled file, so I renamed it to .mp3 and all worked, now just using audacity to split the tracks, thanks for the speedy replies!

---

