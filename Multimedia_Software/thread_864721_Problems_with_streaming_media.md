---
title: "Problems with streaming media"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Guzman85 on 2008-07-19
Hello there, I am new to the forums and this is my first post. 
I'm also new to Ubuntu, I installed it just a week ago and im still learning my way around it.

Well my problem is the following; I'm running Ubuntu Studio and, although videos and music play just fine (using Totem or Audacious), and streaming videos play fine as well, when I open a streaming video (for instance, on youtube) and leave it paused, if I try to open some local media from my computer while I wait for the youtube video to load, it doesnt work. In example, if i try to listen to an mp3 trhough audacious while i wait for the utube video to load, Audacious doesnt play anything. If i try watching some video through Totem I only get a frozen image and no audio. The desktop sounds don't work either.

I must stress that audio and video does work if im not watching any streaming media on firefox.

If anyone can provide some advice on these matters, or a solution to this problem, I would be grateful.

Sorry for my bad English, im not a native speaker.

---

### Post by wolfen69 on 2008-07-20
try:
```
sudo apt-get install libflashsupport
```

---

### Post by BoneslikesLinux on 2009-04-29
I'm using Hardy and could not stream video from anywhere...youtube etc, I updated Flash still no go and found the problem was Adobe Flash Player 10. I downloaded a version of 9 and installed it and bingo !! all works. So it seems there are a few issues with Flash 10

---

### Post by chudder on 2009-04-30
> **BoneslikesLinux said:**
> I'm using Hardy and could not stream video from anywhere...youtube etc, I updated Flash still no go and found the problem was Adobe Flash Player 10. I downloaded a version of 9 and installed it and bingo !! all works. So it seems there are a few issues with Flash 10

I don't quite have the same problem but I'm wondering if it's the same cause.  My problem is that I just installed Jaunty and I was using Intrepid which worked great.  Jaunty works fine too except for the processor(s) (pentium dual-core) are working a lot harder when streaming flash video as compared with Intrepid.  I was wondering if it's because of Flash Player 10.  I don't even know which flash version I have.

Any insight would be great!

Thanks

---

### Post by chudder on 2009-04-30
> **chudder said:**
> I don't quite have the same problem but I'm wondering if it's the same cause.  My problem is that I just installed Jaunty and I was using Intrepid which worked great.  Jaunty works fine too except for the processor(s) (pentium dual-core) are working a lot harder when streaming flash video as compared with Intrepid.  I was wondering if it's because of Flash Player 10.  I don't even know which flash version I have.

Any insight would be great!

Thanks

Okay, so I found out I didn't have Flash Player 10 even installed, I installed it through synaptic and it works a little better but still a bit choppy, the processors are still working pretty hard.

---

