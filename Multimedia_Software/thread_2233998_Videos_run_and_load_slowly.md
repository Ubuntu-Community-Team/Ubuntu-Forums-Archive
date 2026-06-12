---
title: "Videos run and load slowly"
date: 2014-07-11
forum: Multimedia Software
---

### Post by dylan0005 on 2014-07-11
Hello again everyone!

I got another issue, this time about online-videos.... the graphic part doesn't run pretty well, is slow, while video is playing looks like If it had a buffering problem but it doesn't, the audio sounds good(I mean it runs in normal way) but the graphics are slow so it looks terrible!
 
Anyway what I did was that I opened the monitor system and the CPU ran with 100% during playing the video, **Is that a clue?**    

So my question is** What could it be the problem?** I mean I have no problem with RAM . I'd appreciate any help...

Os: Ubuntu 12.04 LTS
Web-browser: Chromium
Web-pages: youtube, tutv, dailymotion etc...

---

### Post by patsev-anton on 2014-07-12
lspci -knn | grep VGA -A2

---

### Post by Vladlenin5000 on 2014-07-13
If it's the same machine you posted about here - [http://ubuntuforums.org/showthread.php?t=2232576](http://ubuntuforums.org/showthread.php?t=2232576) - then:

1) this thread is duplicate. The problem is the same and you'd be better off by actually following up the other thread. That alone is a problem - it dilutes community efforts - and on top of that the almost non-existent hardware/drivers information results on other users having to - again - ask about it (post #2). Nevertheless the most important part is below because...
2) it won't play any HD content no matter what you do or don't, no matter what distro, Ubuntu flavor, whatever,... and
3) it'll stutter with many SD content depending on the codec.

---

### Post by dylan0005 on 2014-07-14
uh... Thank you for your observation, and for answering your question: Yes it is the same machine information. The issue's description of the other thread is maybe related to this but the problem differs in terms of what thing is causing the objection so before was audio, this time is video-graphics.
 
I don't want to watch videos with HD, While videos can play without problems I'm happy because I know my pc limitations so I don't want my pc to do something it can't. 

Whatever, If you really think this thread is duplicate, just leave your comment about it and I'll follow up the other one. I'm really new in this forums I just look for help to solve technical problems and maybe that info can helps other users to solve theirs.

---

### Post by Vladlenin5000 on 2014-07-14
You should follow up the other one no matter what. People have invested some of their time trying to help you or at least explaining what are the realistic expectations* for that computer. Instead of following up you decided to open a new one even more cryptic/vague and on top of that you totally ignored the post #2. It would have been much better if you had ignored me and instead posted the results of the requested command. Even better is when people don't need to ask such informations.


* In a nutshell, your computer is weaker than the common 'netbooks' in the  market circa 2008-2009 therefore you should set your expectations  accordingly

---

### Post by dylan0005 on 2014-07-14
You're right, My apologizes for the post #2 pasev-anton.. I completely forgot it. After a while of searching & trying solutions I didn't succeeded but it looks like the problem has gone.
I know the computer is weaker than others that's why I just trying it getting back to life...
Anyway, Thanks for your comments and suggestions I really appreciated them. I'll close the thread.

---

### Post by lae2 on 2015-05-26
the same problem on Ubuntu 14.04.2, firefox 38.0, compaq presario cq61

lspci -knn | grep VGA -A2 				

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G98M [GeForce G 103M] [10de:06ef] (rev a1)
    Subsystem: Hewlett-Packard Company Device [103c:306a]
    Kernel driver in use: nouveau

---

### Post by SeijiSensei on 2015-05-26
I'd start by installing the proprietary driver for your NVIDIA card.

---

### Post by lae2 on 2015-05-26
tried but crashed

---

### Post by SeijiSensei on 2015-05-26
Did you use the "Additional Drivers" application within Ubuntu?  If you tried installing using any other method, try again.

From the command prompt you can use:
```
sudo apt-get install nvidia-current
```

---

### Post by lae2 on 2015-05-26
I did but after half hour the entire sistem is crashing down and i need to power on again.

Thanks.

---

### Post by SeijiSensei on 2015-05-26
After half-an-hour?  So the machine booted correctly with the NVIDIA driver, but crashed sometime after that?  Sounds like overheating or bad memory then.  What do you see in /var/log/syslog at the time of the crash?

---

### Post by lae2 on 2015-05-26
yes sir, only with nvidia

i tried now first time but     bash: /var/log/syslog: Permission denied
 need to use sudo?

one notice, I tried nvidia before to post here, now I use xorg

---

