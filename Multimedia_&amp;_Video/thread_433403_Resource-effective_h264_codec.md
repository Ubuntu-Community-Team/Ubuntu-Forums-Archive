---
title: "Resource-effective h264 codec"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by WanderingKnight on 2007-05-04
Here's my question: Are there any non-processor crippling h264 codecs available for Linux? (a la CoreAVC in Windows, which enabled you to run any HD h264 video with amazing effectiveness with a modest system). I use mplayer, and I have the codec pack that's offered by the makers of mplayer themselves. It enables me to run h264, but with terrible performance in most cases.

Any suggestion will be gladly received.

---

### Post by MrWizard on 2007-05-11
> **WanderingKnight said:**
> Here's my question: Are there any non-processor crippling h264 codecs available for Linux? (a la CoreAVC in Windows, which enabled you to run any HD h264 video with amazing effectiveness with a modest system). I use mplayer, and I have the codec pack that's offered by the makers of mplayer themselves. It enables me to run h264, but with terrible performance in most cases.

Any suggestion will be gladly received.

Hi WanderingKnight.  Great question.

I just compiled mplayer from source and it seems they've been making improvements.  I have a decent machine (Core 2 Duo E6600 with 2 GB of RAM), so it is hard to say what will or will not work for you.  But, a fresh build of mplayer from SVN was able to play things which previously barely maxed out my CPU, and at around 60% CPU utilization on average.  So, again, quite an improvement.  The version in the feisty repos looks to be about 6 months old.

Anyway - that's just a thought.  Another thing to consider is the mplayer from SVN was patched to allow integration of CoreAVC on i386 machines.  I haven't attempted that.

Feel free to ask more questions - who knows if I can actually answer them, but I'll give it a whirl! :)\

- MrWizard

---

### Post by andrew.46 on 2007-10-23
Hi,

 Your question was a while ago and perhaps you have found the answer:

> **WanderingKnight said:**
> Here's my question: Are there any non-processor crippling h264 codecs available for Linux? (a la CoreAVC in Windows, which enabled you to run any HD h264 video with amazing effectiveness with a modest system). I use mplayer, and I have the codec pack that's offered by the makers of mplayer themselves. It enables me to run h264, but with terrible performance in most cases.

Any suggestion will be gladly received.

 You would be best to run both the svn mplayer and svn h264. There is a walkthrough on these forums that demonstrates this:

[http://ubuntuforums.org/showthread.php?t=558538&highlight=howto+svn+mplayer](http://ubuntuforums.org/showthread.php?t=558538&highlight=howto+svn+mplayer)

 Actually it is *my* walkthough :) The section on H264 has only just been added and I am using it myself with great success.

                    Andrew

---

