---
title: "XBMC + Intrepid. Anybody have any issues?"
date: 2009-01-10
forum: Multimedia Software
---

### Post by Roasted on 2009-01-10
I just installed XBMC and I was watching some videos through it and it seems to be relatively unstable. At one point my girlfriend said, oh, rewind I want to hear that again! I clicked to go back and suddenly my computer sounded like a broken record player, playing a nanosecond worth of a bass tone repeatedly at a fast rate of speed.

On another instance the video simply went at warp speed with no sound and wouldn't play at typical watching speed. 

Is it just me?

Ubuntu 8.10 64 bit.
Nvidia 9600GT 512mb.
Intel Quad Core 2.33ghz.
4gb DDR2 800mhz RAM.

---

### Post by hikaricore on 2009-01-10
I'm going to assume you're using the ppa packages they've made which are very outdated.
What you'll need to do is compile the latest build from source and you'll have much better performance.

[http://xbmc.org/wiki/?title=HOW-TO_compile_XBMC_for_Linux_from_source_code](http://xbmc.org/wiki/?title=HOW-TO_compile_XBMC_for_Linux_from_source_code) 

I have no troubles aside from the occasional crash which I assume has to do with the few remaining pulseaudio bugs.

If you can't deal with a little bit of instability which you're going to see in XBMC (as the linux port is still a work in progress),
you may want to look into using mythtv with the mythvideo plugin, it's rocksolid but less pretty to look at.

---

### Post by Roasted on 2009-01-10
Well, imagine that. I hit refresh twice. First time, no response. Second (a second later) BAM, there you are. Ha.

Yes, I am using the PPA packages. I was not aware of the age of them. I will remove them and follow your guide tomorrow. Thanks for the response.

---

### Post by hikaricore on 2009-01-10
_xbmc - 8.10final1-intrepid4_     **2008-11-15**

As you can see they're not super old, but they are 2 months back from the current code.
The XBMC team has made some fantastic advances in their pulseaudio integration.  ^_^

---

### Post by Roasted on 2009-01-11
Why would 2 month old code constitute it as "outdated"? I mean, I'm having some pretty unstable results here. I can see if I'm using XBMC that was made for Feisty on Intrepid, but, still... 2 months old when Intrepid was released 3-4 months ago? I didn't think that'd be the case...

Aw man, I just noticed... I'm running 64 bit Intrepid. Would that be a problem with XBMC???

---

### Post by hikaricore on 2009-01-11
I think you missed my point.
The code for XBMC has been updated many many times (several hundred?) since those packages were built.
Many of the bugs in the ppa builds that that XBMC team manages have been fixed.

Here's a full list of recorded changes in the last two months: [http://xbmc.org/trac/timeline?from=01%2F11%2F2009&daysback=60&changeset=on&update=Update](http://xbmc.org/trac/timeline?from=01%2F11%2F2009&daysback=60&changeset=on&update=Update)

As far a 64bit is concerned I've no clue but I don't imagine it would be an issue.
Build the thing from source and see if it fixes some of your issues. :p

---

