---
title: "MPlayer: Slow on GUI, fine on terminal"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by Fehrant on 2008-04-10
First off, I'm a total newbie to ubuntu. I have used Fedora a bunch of times before, but quite frankly it'd be safe to say I don't know anything. 

Now, I had to configure several things, and between ubuntu forums and google, I pretty much had it sorted out. It was very gratifying being able to solve things on my own. This issue however I have searched, and while I find similar stuff, I still cannot find a solution.

My issue is the following: I downloaded VLC and was ok with it. The only thing I had against it was the fact that if you start seeking in a .mkv it crashes. This seems to be something that just happens with VLC, so I decided to give MPlayer a try. After sorting out some initial issues, I got the the point where it could output video and sound. The sound is fine, the video is too slow. I tried all the vo devices listed, but I still got the same result. What surprises me is that when I try from the terminal, it works just fine.

---

### Post by DynamicMouse on 2008-04-11
I had the same trouble, I think the problem was that in the gui it was using some config file that decided to use -vo gl or -vo gl2 and the openGL stuff was a bit naff on my system.  I'll have a look for the config file when I get home

---

### Post by Fehrant on 2008-04-13
Don't mean to shameless bump the thread, but could anyone shed light into this matter? Perhaps point me in the right direction? Thanks.

---

