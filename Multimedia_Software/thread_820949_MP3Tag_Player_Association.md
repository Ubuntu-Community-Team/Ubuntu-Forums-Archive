---
title: "MP3Tag Player Association"
date: 2008-06-06
forum: Multimedia Software
---

### Post by pirabu on 2008-06-06
I use the free tagging tool MP3Taqg extensively. When I switched over to UBUNTU I installed MP3Tag using Wine and using it. Here is my problem.

When I double click a mp3 file from MP3Tag i get an error message saying there is no player associated with the file. So I went to the MP3Tag Options panel and try to get RhythmBox or Amarok as a player. Now I got RhythmBoc associated successfully. But when I double click a file it opens up Rhythmbox successfully but in paused mode. When I press ply it randomly starts some song (not the file I have double clicked). So I think I am missing some parameter to pass to Rhythmbox when I call it. It parameter it would be ?

And Where can I locate the executable file for the Rhythmbox installed? They said in /usr/bin. But not there.
:guitar:

Any help would be greatly appreciated.

---

### Post by nick_h on 2008-06-06
The executable is /usr/bin/rhythmbox - type:
```
which rhythmbox
```

---

### Post by pirabu on 2008-06-09
Ok. Now I got the Rhythmbox to pop up (start) when I double click a file from MP3Tag. But here is the problem. It starts as paused and when I click play it just starts playing the track it was playing last. Not the song that I ahve doubleclicked to start with. There is a box in MP3Tag for parameter. Anybody knows what parameter to pass?

---

### Post by nick_h on 2008-06-09
You need to use *rhythmbox-client* rather than *rythmbox*.
```
rhythmbox-client --enqueue filename --play --next
```
--enqueue adds the file to the Play Queue
--play ensures that Rhythmbox is playing
--next moves to the next song on the playlist

For details type:
```
man rhythmbox-client
```

I'm not sure that you want the --next though - it might mess things up if you want to enqueue a few songs in a row.

I think there are some nautilus plugins to do this sort of thing.

---

