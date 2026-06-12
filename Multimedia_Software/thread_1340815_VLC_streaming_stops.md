---
title: "VLC streaming stops"
date: 2009-11-29
forum: Multimedia Software
---

### Post by omnipotentperson on 2009-11-29
I am trying to stream video from [stagevu]("http://www.stagevu.com") with VLC. When I start the streaming, the video plays for up to 6 seconds before stopping with no explanation. When I ran it in terminal, I saw that it continuously prints "header damaged" interspersed with "[0x85624c0] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)".

I have looked around online, but no one else seems to have the same problem. I am quite inexperienced with streaming videos, so can anyone help me?

---

### Post by mc4man on 2009-11-29
In this case I think the issue is the video is on a crappy server.(may work better at diff. times of the day

You can playback if you click on the 'download' button  which should open up a new window and play.

If you have the 'totem-mozilla' plugin installed it probably will play, the gecko-mediaplayer plugin would  work better here ( buffers better than totem-mozilla, only have one or the other installed at a time

Maybe easier to just dl. and play locally
```
wget http://n60.stagevu.com/v/e47976079ecf56ed066a19a79598e2d6/kcvfftzacooa.avi
```

(r.clicking on the dl. button -'copy link location' gets you the url

---

### Post by omnipotentperson on 2009-11-29
I don't think the problem is with the server. MPlayer can play the videos, although they are very jerky. The only problem is that I can't pause. VLC stops playing and never starts again...

---

