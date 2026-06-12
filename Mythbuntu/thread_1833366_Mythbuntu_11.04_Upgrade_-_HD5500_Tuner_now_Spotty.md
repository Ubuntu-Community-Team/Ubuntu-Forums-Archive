---
title: "Mythbuntu 11.04 Upgrade - HD5500 Tuner now Spotty"
date: 2011-08-25
forum: Mythbuntu
---

### Post by Nausser on 2011-08-25
After upgrading from Mythbuntu 10.10(which had issues that 11.04 fixed) to Mythbuntu 11.04, my PCHDTV card's recording quality took a turn for the worst. The HD5500 still works for my QAM/local HD channels for the most part. Although, it is to a point where I can't really use it anymore because the recordings that the card executes, have a lot of artifacts and digitization(if you want to call it that) as well as some audible, high pitched blips. Another trademark is some "tearing" of the video stream. I don't know how else to describe it. I've downloaded the full mpg to another computer and the artifacts are still there. This tells me it is being recorded this way. All I know so far is that with previous versions of mythbuntu, the HD5500 recorded my QAM channels perfectly. Now it does not. Not very good for one of the few HD cards that is supposed to work out of the box with Linux.
I couldn't find a post with this happening to anyone else so I've started my own.

If I am the only one experiencing this, then please point me in a direction to maybe re-install the card from scratch. I'm not sure if that would be a necessary or good idea since the card is natively supported in the kernel... I think.

Also, if anyone reads this that is running Mythbuntu 11.04 with a pcHDTV HD5500 card that is recording QAM just fine, I would like to know that as well.

---

### Post by klc5555 on 2011-08-26
Mythbuntu 11.04 runs a 2.6.38 kernel and related v4l-dvb kernel drivers. While I use 3 pchdtv-hd5500 cards, with two of them on Mythbuntu, it is an earlier version than 11.04.

I do however have one hd-5500 running on a 2.6.38.8 (home compiled) kernel and locally compiled v4l-dvb drivers (on a Slackware box) that works flawlessly for QAM.

Usually when you start getting pixellation/artifacting on one of these hd-5500 cards, it's a signal strength issue. When tuning live-tv on QAM, the displayed signal-strength needs to be well over 80% (best over 90%) to avoid these problems. 

There are usually two potential causes for signal-strength problems: 1) a cabling issue, e.g. the silly friction-fit cable connection has come part-way out the back of the card and has to be reinserted; a cheap splitter is giving the card's input a disproportionately small amount of the signal; or some of the coax connections have loosened and need retightening; or something similar.

Or 2) sometimes the particular iteration of a v4l-dvb driver may have amplification issues.

So if potential cabling issues can be completely eliminated as the cause, but the pixellation problem remains, there are usually a couple of ways the signal-strength issue can be approached. The first is to add a small inexpensive line drop amp (Motorola or similar) to the cable input to your box at some point. I use this solution on the Mythbuntu box with two pchdtv-5500s: one card is fine on its own, the second (as it has aged over the past 4 years) will pixellate and artifact without the amp. With the amp both cards are fine.

Another possible attempt, if you've become convinced that the issue is software and not signal-strength hardware-related problems, is to compile and install your own v4l-dvb kernel drivers from linuxtv.org. Either current ones, or slightly older iterations from around a year or so ago (from around the era of Ubuntu 10.04 or 10.10). Simple enough to do, even in Ubuntu, though if it works the downside would be that you'd need to recompile and reinstall the drivers after Ubuntu's all-too-frequent kernel/module updates.

Anyway, this is the catalog of potential problems and solutions that I can see for pixellation in the 5500.

---

### Post by Nausser on 2011-09-01
Thank you very much for your suggestions. I will check them off the list as soon as I find time.

---

