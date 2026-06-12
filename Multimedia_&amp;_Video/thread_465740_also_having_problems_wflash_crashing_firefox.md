---
title: "also having problems w/flash crashing firefox"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by devapea on 2007-06-06
Hi newbie. 1st post. 

the second I try to play a video on youtube firefox freezes.  I tried a few things that were posted earlier by steveneddy.  

Changing the firefox file in the terminal, getting both adblock and flashblok, adding alsa -oss but still I get the same result.  Ive had this problem for several days now and I just got the ubuntu firefox updates and still same result.  I'm using the  9.0.31.0.2ubuntu1 (flashplugin-nonfree)  I saw that adobe was working on the prob. and hopefully not too many people have this issue.  

Thanks in advance for the help and yes forgive me I'm new to this but I still totally love linux, ubuntu and the whole shmear.

---

### Post by eggdeng on 2007-06-06
You could try following the steps under 'Installing from the Adobe website' at [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)  Worked perfectly for me.

---

### Post by DagMan on 2007-06-06
I'm finding two similar solutions reported.  I've only just applied one so don't know if it will work but [http://ubuntuforums.org/showthread.php?p=2787287#post2787287](http://ubuntuforums.org/showthread.php?p=2787287#post2787287)
and 
[http://ubuntuforums.org/showthread.php?t=286069&highlight=flash+firefox+crash](http://ubuntuforums.org/showthread.php?t=286069&highlight=flash+firefox+crash)

The first link is a newer post.

---

### Post by bobbybobington on 2007-06-06
Yeah this is a common problem. Firefox likes to crash in general. Hopefully they'll smooth things out.

---

### Post by devapea on 2007-06-07
Thanks guys. I'll give it a whirl and report back.  Linux community rocks!

---

### Post by devapea on 2007-06-07
thought I'd update ya'all with my crashing.  After much reading of every post out there that talked about the conflict with adobe and flash and firefox crashing and how it seems to be a bug that adobe is looking into.  Folks been saying that disabling sound is a workaround.  After putting dents on my keyboard from banging my head against it I found my solution.  I guess basically this is similar to disabling sound.  

Im using ubuntu fiesty fawn - **go to system-preferences-sound.  In devices I changed all to OSS.** 

Open sound system which is older and not as good as Alsa but hey it fixed my issue with flash on youtube.  Before this I would just go to youtube and select a video and my firefox would freeze up forcing me to do a forcequit.  

I tried many tings- getting adons for firefox that would weed out flash ads.   deleting firefox plugins. installing nonfree flash.  I did everything but burned incense and prayed to the Gods of  ubuntu flash and  firefox.    

I'll letcha know if things change. Still lovin the linux

---

