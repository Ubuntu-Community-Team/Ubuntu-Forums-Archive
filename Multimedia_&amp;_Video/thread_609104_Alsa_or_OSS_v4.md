---
title: "Alsa or OSS v4"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by GinKen on 2007-11-10
Hi, 
I have been having big problems installing Ubuntu Studio which I reported here
[http://ubuntuforums.org/showthread.php?p=3745711#post3745711](http://ubuntuforums.org/showthread.php?p=3745711#post3745711)
Researching these forums to try to solve the problem over the last week has introduced me to many things I didn't know, and I have questions, though all stemming from the same problem, seem to fall into different categories, which I've posted to different forums.  The topic of sound cards seems appropriate to this forum, so what I would like to ask here is any opinions of which is better, Alsa or OSS v4. Also, how important is timidity in Ubuntu multimedia apps, are there alternatives to timidity, or can timidity be set to work with oss v4 rather than alsa.
Basically, the problem I am having is where Alsa has problems(link above) recognizing the Sigmatel sound card on this Dell Inspiron 1721, so no sound, even in Recovery mode, the OSS v4 I downloaded seems to work fine in providing sound.
Could really use some help here.
Thanks!

---

### Post by Yellow Pasque on 2007-11-10
It depends on the card, really. Some are supported better in ALSA, and some in OSS. In terms of simplicity and ease of use, OSS wins IMO and the ossxmix program is superior.

Look through this list to see what's supported by OSS: [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)

Personally, I use an M-Audio Revo 5.1 and it's supported much better under OSS (all the jacks work, no volume bugs)

---

