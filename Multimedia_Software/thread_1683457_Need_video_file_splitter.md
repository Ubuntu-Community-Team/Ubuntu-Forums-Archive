---
title: "Need video file splitter"
date: 2011-02-07
forum: Multimedia Software
---

### Post by Silvernail on 2011-02-07
I need recommendations for a video file splitter. Googling for 'video file splitter' returns 84,000 results, none of which I recognise from a know website.

Searching this website returns no results of 'video file splitter'.

What I have is 80 tapes from a Sony HI-8 CamCorder. I have extracted those to an AVI file and converted to a MP4. These tapes run from 48 mins. to an hour and 48.  They are lessons from a fly tying class that my fishing club conducts. Some date back to '92. Each tape/file will consist of one subject, such caddis flies. There will be illustrations on tying several stages of the life cycle.

I would like to break each tape into chapters by life cycle.

In the repository there is 'Wavbreaker File Splitter', something similar for video would be ideal.

Any suggestion on where/what to look for?  Your experience with such an animal?

TIA
Dave

---

### Post by ajgreeny on 2011-02-07
What you need, by the sound of it is a simple video editor such as avidemux, or pitivi, the second of which is already in 10.10, I think.  I have used avidemux, but not pitivi, so can not compare them, but I quite liked avidemux when I used it.

---

### Post by Jose Catre-Vandis on 2011-02-07
```
ffmpeg -i input.file -ss 00:03:00 -t 300 -acodec copy -vcodec copy output.avi
```

This will make a copy of the section starting three minutes in (-ss..)and 5 minutes long (-t...)

---

### Post by Silvernail on 2011-02-07
> **ajgreeny said:**
> What you need, by the sound of it is a simple video editor such as avidemux, or pitivi, the second of which is already in 10.10, I think.  I have used avidemux, but not pitivi, so can not compare them, but I quite liked avidemux when I used it.

File I'm currently  working:
-rwxrwxrwx 1 dave dave  2881619746 2011-02-07 15:12 Bass_Bugs_by_Bill_Gammel.avi

I would like to have a time line like 'pitivi', but it crashes with the above file.

Avidemux give me an error when trying to load but does not tell me what is wrong.

I have "kino' converting it to DV, started 1:26 minutes ago.

So far have tried: LIVES, Open Video Editor, Project X, Videocut.
Thanks for your input. If you find anything else, let me know.

---

### Post by Silvernail on 2011-02-07
> **Jose Catre-Vandis said:**
> ```
ffmpeg -i input.file -ss 00:03:00 -t 300 -acodec copy -vcodec copy output.avi
```

This will make a copy of the section starting three minutes in (-ss..)and 5 minutes long (-t...)

Just saying without any facts, the problem may be the file is too large and I have to break it into workable size units.

Each chapter is differents lengths. I really need a time line I  can scan and see when the tyer puts a new hook in the vice. That will be the chapter break.

Your code snippet just got stuck in my script file.
Thanks
DAve

---

### Post by Jose Catre-Vandis on 2011-02-09
Then watch it with mplayer, use the OSD (**Press O**) and **<** and **>** to go forwards and backwards. Use  **.**  to move forward frame by frame  (Sorry, no backwards frame by frame) Look up **edl** for setting cut points.

If your video is mpeg2, try **ProjectX**

---

### Post by Silvernail on 2011-02-10
> **Jose Catre-Vandis said:**
> Then watch it with mplayer, use the OSD (**Press O**) and **<** and **>** to go forwards and backwards. Use  **.**  to move forward frame by frame  (Sorry, no backwards frame by frame) Look up **edl** for setting cut points.

If your video is mpeg2, try **ProjectX**

Will try. Thanks.

---

