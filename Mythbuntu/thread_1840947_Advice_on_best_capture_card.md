---
title: "Advice on best capture card"
date: 2011-09-08
forum: Mythbuntu
---

### Post by danince on 2011-09-08
I have recently been forced to rebuild my entire myth box from scratch and have decided to go with mythbuntu this timer around.  I am looking  to get a capture card that just works.  I live in the US and I need to have the ability to accept standard analog cable over the wire and input from a cable box over svideo or something similar.  This is going to be a backend only solution, so I do not need a remote solution but I may need a ir blaster to control my cable box if I can not get firewire to work. I have read the posts on the working/non working hardware configurations, but a lot of those working solutions seem to be out of date.  Any advice on this would be greatly appreciated.

---

### Post by mookie60 on 2011-09-10
D,

As I'm currently looking to find a better tuner than what I have, I thought I'd add my two cents.

1600:

I started about 3 yrs ago with a Hauppauge 1600.  The analog tuner has always worked out-of-the-box.  It has always done a solid reliable job, if a tad grainy/blurry.  Too much signal strength increases increases the graininess, so I run the cable through a couple of splitters first.

The digital QAM tuner is another matter; it needs a strong signal (don't go by the signal strength meter displayed when changing channels - it always reads zero).  It does ok on SD digital channels, but HD channel recordings have a greater tendency to stutter/pixelate.   It's tolerable most of the time, but just barely.  

Because the QAM tuner needs a strong signal, I use an amp as it exits the wall.  The strongest signal is sent to the QAM.  The cable to the analog side must be run through a couple of splitters to drop the power.   It's kind of a pain to balance it out after making wiring changes.


150

I've had a Hauppauge pvr-150 about 2 years.  It's been totally reliable.  It has a similar issue with graininess, the signal power can't be too much, or too little.  The recording quality is a bit better than the 1600, but not by much.

Both cards (1600 and 150) have svideo inputs which I've only recently tried, unsuccessfully, to use.   As I can't get either to work so I'm pretty certain the problem to date is due to operator error.


PCHDTV 5500

Purchased this about a year ago, hoping to get better QAM recordings.  I had high hopes as I'd heard good things about it. 

The analog tuner only worked for about 2-3 months, then died.  As I still had the other analog tuners, I didn't pursue a replacement.

The digital QAM tuner has always made beautiful HD recordings, way better than the 1600;  that is until about a month ago.  Now the computer no longer sees the tuner, at all.  I can't be sure, but I guess it died.   Searching this site for "5500" did not pull up any recent postings of the problem, so I'm assuming it's not related to a kernel update.


So I'm in the market for a digital/QAM tuner(s).  I'm probably going to try the HD Homerun Dual. 

Hope this was of some use.

---

### Post by tmcgary on 2011-09-11
I wanted to second much of what mookie60 said about the 1600.

I have used mine for about 3 years. It is sort of a pain to use the QAM side from channel scanning at set up all the way through recording and live tv viewing mostly because of the need to a really strong single. I use a power inline amp and it just barely works. The setup is seems to be more difficult also because I use DTV straight out of the wall without a cable box.

I will be purchasing an HDHomeRun in the next year or so. Hope this helps!

---

### Post by klc5555 on 2011-09-11
I have 3 pctv-hd5500s and four Hauppauge 1600s.

I have never had any particular trouble with the 5500s, which I've owned since 2007. One has begun to require a slightly stronger signal than the others, and so the machine it's on has a small line drop amp. Otherwise, flawlessly reliable. I don't do analog on them any longer, as they only have the one input which obviously can't be hooked to both an analog cable-box output and a direct QAM connection simultaneously. For that reason I started trying to use the Hauppauge 1600. 

I bought the my first 1600 in 2008, and thought initially that it was next to useless, both for analog and especially for digital. But I was wrong. The problem at the time was the cx18 driver was not ready. By mid-2009 the cx18 driver could reliably give a good analog recording, much better than the oddly beloved PVR-150, but the digital side of the card was essentially deaf.

But by around August 2010, the digital amplification problem was taken care of in the cx18 driver, so if you're using a driver set much later than this, you're in business. The Hauppauge 1600 is now my preferred card, and I get flawless HD and analog recordings with my four. I can't use an amp on them any longer --signal strength is too high and my old amp swamps the signal.

That said, I only use older units of this card. They have a variety of analog tuner models in them, and the the cx18 developers run a bit behind in ironing out support for the up-to-the-minute 1600 models.

---

