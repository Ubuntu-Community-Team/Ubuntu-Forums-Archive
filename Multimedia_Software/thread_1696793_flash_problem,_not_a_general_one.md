---
title: "flash problem, not a general one"
date: 2011-02-27
forum: Multimedia Software
---

### Post by HeadHunter00 on 2011-02-27
i got the weirdest flash player problem on the planet. so, here's what the problem is. whenever i play low quality 360p flash videos in fullscreen in firefox, i get horrible performance and it eats up all the cpu resources, as compared to 1080p fullscreen video, which is smoooooooth and doesn't take up as many resources as low quality videos. why is that? anyhoo, i am using flash 10.2 beta 64 bit and have 64 bit ubuntu, but the problem persisted even on the stock flash player.

---

### Post by houseworkshy on 2011-02-27
I haven't got a clue but I'll watch this thread, interesting.  Just as an experiment have you tried putting in one of the firefox youtube downloader addons, then tried playing both types of file locally.  Or crawl around the internet archive and see how differant video file formats perform ( some good stuff there anyway ...been watching Will Hay films and Tony Hancock episodes, before my time so new too me ... highly amusing )

I've never heard of anything like that before, seems the wrong way round.  Will watch with interest.  Maybe try various players too and mention which player your browser is set to call.

---

### Post by HeadHunter00 on 2011-02-27
once i download the videos, they work just as they were intended to. 1080p video eats up a lot more resources than 360p. and the 360p video runs smooth, even with a load of 100 percent on all cores (not right on but close to).

---

### Post by HeadHunter00 on 2011-02-27
oh, and if i use html5, 360p videos run fine, but only chrome has forced html5 support, and i dont like using chrome.

---

### Post by houseworkshy on 2011-02-27
I have no advice to offer but will pop back to see what other people say.  Hmmm  maybe something else is in the stream with the low def video...splitting?  netstat or wireshark could be informative.    

It is certainly curious and I think you may have earned the weird flash problem of the year award.  I'll pop back sometime and see what more informed people say or bump the thread if none have yet.

---

### Post by HeadHunter00 on 2011-02-27
well, i think you saw this one comping, but turning off compiz solves it. but still, its so weird that hd videos run faster than low quality videos, it makes no sense. i will try to figure out if there is a specific addon in compiz which causes this.

---

### Post by HeadHunter00 on 2011-02-27
ok dude, you wont believe which application was the actual culprit, its cairo-dock. when i turned it off, everything was back to the way it should be. full screen flash videos were running full speed. so weird. so, either turn off compiz or cairo-dock. guess i earned the weirdest flash problem and the weirdest solution award of the year. lol. also, it doesnt matter if you run cairo dock with or without opengl.

---

