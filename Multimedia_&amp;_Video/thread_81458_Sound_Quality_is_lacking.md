---
title: "Sound Quality is lacking?"
date: 2005-10-24
forum: Multimedia &amp; Video
---

### Post by groovywombat on 2005-10-24
I had been using ubuntu for a couple of weeks, and the other day I was using my mom's windows box, and i started to play some mp3s, when i noticed that the sound quality was much better than on my computer with ubuntu.  just much cleaner sounding, now as i lsiten to music on my ubuntu box, it sounds muddled and well, shitty.  I have AC97 onboard audio, but it's going through a solid state receiver with high end klh speakers and sub.  now when i boot into windows, on this machine, it sounds great.  This has now become another problem with me using linux, I already can't get my RAID0 working, and now I am unhappy with the sound quality.  so maybe someone can help me with this sound problem. 
thanks

---

### Post by Kyral on 2005-10-24
Try this page and see if it helps

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by groovywombat on 2005-10-25
thanks kyral
but perhaps i'm missing something, but the wiki seems to deal with really bad or no sound at all.  My sound is acceptable, it's just not what it should be, well it gets better when I turn the volume way up, but that tends to aggravate others i think.  I belive I have the correct drivers.  
on another related topic, my sound tends to drop out someties when i'm not using the computer, i'll come back and the PCM volume is way down, perhaps this could be a related issue
thanks

---

### Post by trixtah on 2006-03-30
I think I've hit on the solution. I have a Toshie M2 laptop, which uses the AC97 drivers. The fuzziness with the bass on certain tracks (like Portishead's stuff) was driving me insane.

I installed gnome-alsamixer and had a fiddle. There are several controls, but I found that backing the PCM control off to about 70% of the top setting miraculously cured the problem. I have no idea what the PCM control is for (I know it's a sound sampling method) in the Linux context, but I'm not a Linux techie. :-/

---

### Post by Xiunix on 2006-04-01
I have found that if you enter gnome-alsamixer and run all at about 75% or its yellow-red area, the acceleration on the sound card is not as stressed and the quality is much better. If you find it too quiet however, then maybe you should get a new card.

---

### Post by Fmac on 2006-04-05
I'm getting decent music quality now, with PCM between 3 and 35. I have an external amp that helps out with the volume. It's still flaky, but less so.

Strange thing is, audio from movies in VLC is great. But music - MP3, OGG, FLAC, you name it - from BMP, XMMS, MPD, AmaroK, etc. - is still poor.

---

### Post by jms830 on 2006-04-21
I was having problems with cracking sound, I double clicked the volume icon on my gnome-panel and made sure that PCM was set to between 70-80% volume, and also within XMMS if you go to preferences, then look at your Output plugin and if its the ALSA one, you can click the configure button and make it so that XMMS's volume bar controls MASTER instead of PCM. This helped me out when I was using ALSA.... but now I have other sound problems of my own. But hey, it might help someone else.

---

