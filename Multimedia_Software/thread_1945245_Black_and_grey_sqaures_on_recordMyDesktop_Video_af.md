---
title: "Black and grey sqaures on recordMyDesktop Video after converting it"
date: 2012-03-22
forum: Multimedia Software
---

### Post by reto on 2012-03-22
I tried in many ways to covert an ogv file created by RecordMyDesktop to other formats (mencoder, WinFF, devede) but the resulting video files alway has a lot of little black squares all over the screen.
The ogv file looks fine when opening it with VLC, in Movie Player I have sound but a black screen, in xine only a black screen.

Any idea what this could be?

Cheers,
Reto

---

### Post by reto on 2012-03-23
I tried converting a recordMyDesktop generated file on another computer. I have the same problem converting the ogv file to avi. But I can whatch the video in movie player.

mecoder gives the following messages

```

Pos:   0.1s      2f (22%)  0.00fps Trem:   0min   0mb  A-V:0.007 [0:0]
[VD_FFMPEG] DRI failure.
Pos:   2.3s     35f (22%)  0.00fps Trem:   0min   0mb  A-V:-0.133 [533:75]]

1 duplicate frame(s)!
Pos:   3.1s     45f (22%)  0.00fps Trem:   0min   0mb  A-V:-0.133 [424:75]

1 duplicate frame(s)!
Pos:   3.8s     55f (22%)  0.00fps Trem:   0min   0mb  A-V:-0.133 [356:75]


```

The last mesage appears many times.

---

### Post by reto on 2012-03-24
I've updated to ubuntu 12.04 and I can now successfully convert the ogv to avi. The messages about DRI failure and duplicate frames are still there, but the squares all over the image went away.

---

### Post by dastrn on 2012-04-12
I'm having the same issue. I tried converting it with Openshot and ffmpeg and the video still has grey squares everywhere and leaves artifacts as things move around the screen (it's a recorded chess game).

I'm not going to upgrade to 12.04 until it's officially launched. Is there any reason this can't work in 11.10?

The ogv file looks great in vlc. It's just when it is converted that it looks awful.

Someone please help.

---

