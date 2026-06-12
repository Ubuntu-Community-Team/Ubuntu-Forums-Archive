---
title: "Frozen video"
date: 2008-06-22
forum: Multimedia Software
---

### Post by Screwtape on 2008-06-22
Hi, all-
I'm running Hardy on a Toshiba Satellite with an Intel G965 graphics card and I have a very strange problem. In Totem or MPlayer, the video plays extremely slowly for a couple of seconds and then stops dead. It doesn't ask me for a different codec or anything, and it swears it's playing the video, but there's no movement and no sound.

It gets weirder: when I reinstall GStreamer, it works great for a couple of weeks, and then I have the same problem again. Is there a cache somewhere that needs to be cleared every so often? That's all I can think of. Any help would be greatly appreciated.

Your affectionate uncle,
Screwtape.

---

### Post by xc3RnbFO8P on 2008-06-22
Is it related to update?
Did try to play it from terminal?

---

### Post by scriper on 2008-06-22
I have same problem with mplayer from mplayer-nogui package on my ubuntu box. Video stop at the first frame, but i can roll it with arrow keys. Please help.

---

### Post by Screwtape on 2008-07-01
I don't know if it's related to the update or not. How do I play from the terminal?

---

### Post by loud_tiger on 2008-07-02
does this help?

run

> sudo pkill pulseaudio

and try again.

---

### Post by Screwtape on 2008-07-05
Wow, yes, that solved it instantly. Thank you so much! What was that?

---

