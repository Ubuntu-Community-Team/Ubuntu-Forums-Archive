---
title: "Adventures in pcHDTV 5500"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by pteri498 on 2007-12-29
Note: This is useful to test your card to see if it works. This isn't a complete guide to getting anything working, only to see if the card is receiving a signal.

I figured I should post my experiences with this card, so that others need not experience the hell I went through over the past 4 days (WOW, it feels much longer than that).

First off, I've gone though Ubuntu Edgy, Feisty, Feisty using the 2.6.17-10 kernel, Gutsy, and openSUSE 10.3, all in a bleak attempt to get the pcHDTV 5500 card working.

VERY long story short, I could not get mythtv working for me at all. I feared my card was a loss.

I made a fresh install of Gutsy, without the card installed in the computer. After starting it up for the first time, I turned off my computer, installed the card, and started Ubuntu back up. I do nothing more with drivers and such. I use the stock drivers that Ubuntu wants to use.

Then I heard about tvtime, and I promptly downloaded it.

```
#sudo apt-get install tvtime
```

I also found in [this]("http://www.pchdtv.com/forum/viewtopic.php?p=11252&sid=873aba748cecbf703ba693fb1543bae2") forum that in order to get sound with tvtime (as this is only a testing program), I should install sox.

```
#sudo apt-get install sox
```

We can use sox to copy sound from the card's audio device to the regular sound card. Run tvtime, get to your channel of choice, and run the following in a separate terminal:

```
sox -r48000 -c2 -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp
```

Play around a bit with tvtime. For me, the video came in far worse than the regular tv using the same cable, and audio was just awful. I fear that it may be a hardware issue, as I've read such things in a few web pages.

But at least I know I'm getting a signal.


If you run a similar test, please post your results. I'd love to know if this blocky, echoing sound I'm getting is normal for sox.

---

