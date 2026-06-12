---
title: "record radio to mp3 from .smi and .asx stream"
date: 2008-04-05
forum: Multimedia &amp; Video
---

### Post by afeasfaerw23231233 on 2008-04-05
my local radio from radio streaming in .smi or .asx format. but i can't not right click and download it as mp3. how can i record them? here's the link: [http://www.rthk.org.hk/rthk/radio3/earlyshow/20080405.html](http://www.rthk.org.hk/rthk/radio3/earlyshow/20080405.html)
thanks

---

### Post by Ripfox on 2008-04-05
Streamtuner? You can add the preselected stream from "stream" menu then hit "record"

---

### Post by Ripfox on 2008-04-05
Hi

I tried to add both the .smi and the .asx streams to streamtuner as a preselection but it won't tune in to them...could be this crappy internet connection at the hotel i am stuck at though...

---

### Post by afeasfaerw23231233 on 2008-04-05
> **ripfox said:**
> Streamtuner? You can add the preselected stream from "stream" menu then hit "record"

i add the url and it doesn't play

---

### Post by Ripfox on 2008-04-05
Did you add the url or the actual .asx address...like I said I can't tell if it's this connection hats the problem :(

---

### Post by Ripfox on 2008-04-05
I tried streamripper from the command line but that was a no go too :confused:

---

### Post by afeasfaerw23231233 on 2008-04-05
i download the link of .smi and open it with a text editor, i copy the url: rtsp://59.188.18.228/rthk/200804/radio3/05/2008040506.ra and paste
it doesn't work
edit: is there a very easy way to record radio?

---

### Post by Ripfox on 2008-04-05
Usually this works...anyone else? :confused:

---

### Post by ron999 on 2008-04-05
> **afeasfaerw23231233 said:**
> i download the link of .smi and open it with a text editor, i copy the url: rtsp://59.188.18.228/rthk/200804/radio3/05/2008040506.ra and paste
it doesn't work
edit: is there a very easy way to record radio?
That's the correct link to use, but there is a space shown between the 0 and the 5.
That happens on this forum.
To play the station you can use mplayer like this:-
```
mplayer rtsp://59.188.18.228/rthk/200804/radio3/05/2008040506.ra
```

To record the station you can use the dumpstream option with mplayer to save it in ra format or wav format then convert it to mp3.
You can use ffmpeg to convert the ra, or lame to convert the wav.
8)

---

