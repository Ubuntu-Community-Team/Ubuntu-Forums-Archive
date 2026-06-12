---
title: "Youtube, Avidemux and not shaving?"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by Toadmund on 2007-12-01
I want to upload a video I created on Youtube, but it is too long by only 11mb, I'd really like to not shave any material off my film to make it 100mb. (it's now 111mb + ).

Could there be anything I could do using Avidemux to perhaps lower the quality by just a touch, to bring the mb's down just a bit without sacrificing too much quality?

Or should I just shave off a few slices here and there?

---

### Post by ron999 on 2007-12-01
Hi
This is how I would do the job with Avidemux:-
Make sure you keep a backup copy of your video before you start to modify it.
Then start Avidemux and File > Open to load your video.
Then set the Video tab on the left to a suitable codec such as Xvid4.
Then click on 'Configure' underneath the Video tab and then the 'Bitrate' tab.
Set Encoding Mode to Two pass - final size.
And Target FinalSize(MB) to 100MB and click OK.
Leave the Audio tab on the left set to Copy.
Then do a File > Save.
When it's finished, check the quality of the result and the file size.
If it's not right, try again with a higher or lower FinalSize setting.
:cool:

---

### Post by Toadmund on 2007-12-01
Thanks, I'll look into your suggestions when I have consumed less beers.
Tommorow.

Xvid4 was just as an example right?
I just want to use mpeg4 for now, I know (I've read) that mpeg4 is well supported.
:mrgreen:

---

