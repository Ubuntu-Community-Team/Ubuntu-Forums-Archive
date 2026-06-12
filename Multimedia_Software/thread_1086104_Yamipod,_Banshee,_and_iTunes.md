---
title: "Yamipod, Banshee, and iTunes"
date: 2009-03-03
forum: Multimedia Software
---

### Post by woknam66 on 2009-03-03
Ok, I have a couple of questions:

1. It is possible to get iTunes to download podcasts and sync with an iPod touch when using it in Wine with no patches or minimal patches that a braindead monkey could install?

2. I've heard that of the Linux alternatives to iTunes, only Yamipod and Banshee can download podcasts, is this true?

3. How easy is it to download podcasts that are meant for iTunes in Yamipod and Banshee?

---

### Post by woknam66 on 2009-03-03
Ok, a small update, after finding [this]("http://en.wikipedia.org/wiki/Comparison_of_iPod_Managers"), I have some more information. Amarok, Banshee, Floola, gnupod, MediaChest, Winamp w/ ml_iPod plugin, Rhythmbox, and Songbird all allow you to download podcasts, which is all I really need. What I'm wondering now is:

1. Which one(s) have the widest selection of podcasts?

2. Which one(s) can you use to sync with an iPod touch after doing [this]("http://lifehacker.com/388785/sync-your-iphone-wirelessly-in-linux")?

3. How easy is it to get an iPod touch to sync with each of these?

---

### Post by Depressed Man on 2009-03-03
I don't know, but I say iTunes has the biggest podcast list probably (outside of 3rd party websites). But you get those annoying phobos or itms links. So what you can do is..

1) Use PenguinTV. I know that one can handle iTunes links (says so at least)
2) Add podcasts in iTunes, export them into opml, import opml file into almost any music/podcast program (what I do).

---

### Post by woknam66 on 2009-03-03
Thanks, I'll try that tomorrow. What is Phobos and opml?

---

### Post by Depressed Man on 2009-03-03
> **woknam66 said:**
> Thanks, I'll try that tomorrow. What is Phobos and opml?

Phobos is basically Apple's way of masking URLS for podcasts in iTunes. 

[http://en.wikipedia.org/wiki/OPML](http://en.wikipedia.org/wiki/OPML)

Basically it's a standard for porting RSS feeds to any other program. Apple tries to mask the regular urls using Phobos (thus you can't just paste a Phobos link into any podcasting program).

---

### Post by woknam66 on 2009-03-03
Would I have to keep dual-booting if I did this?

---

### Post by Depressed Man on 2009-03-04
> **woknam66 said:**
> Would I have to keep dual-booting if I did this?

Maybe? That's how I do it right now (I don't like iTunes). You could always try using iTunes in Wine or through Virtualbox or any other Virtual Environment? But you'd still have to boot up Windows if you can't get it to work in Wine. 

PenguinTV is suppose to handle itms links so any podcast that links to iTunes should theoretically be put in PenguinTV and then you can also export it to your media program of choice that way too. I just never tried it.

---

### Post by woknam66 on 2009-03-04
I already unsuccessfully tried installing itunes in wine and I don't have ubuntu on a large enough partition to also run a virtual machine within it, so it sounds like opml/phobos is out. I'll try PenguinTV tomorrow.

EDIT: Is PenguinTV an iTunes replacement, or what?

---

### Post by Depressed Man on 2009-03-04
> **woknam66 said:**
> I already unsuccessfully tried installing itunes in wine and I don't have ubuntu on a large enough partition to also run a virtual machine within it, so it sounds like opml/phobos is out. I'll try PenguinTV tomorrow.

EDIT: Is PenguinTV an iTunes replacement, or what?

Not exactly. It's just another podcasting program (kinda like GPodder). Most music programs nowadays have podcasting built in as well. PenguinTv just has the the ability to intepret iTunes links. Though you still won't have access to the podcast store/listings inside iTunes. Not unless you use some other program like that web thing to browse the iTunes store.

---

### Post by woknam66 on 2009-03-04
So I would download the podcasts with PenguinTV and then sync them to my iPod touch with another program?

---

### Post by Depressed Man on 2009-03-04
I couldn't get it to work sadly with phobos links. Maybe ITMS ones will work..

---

### Post by woknam66 on 2009-03-07
Yeah, I've pretty much given up on this. I realized that what I really want is for iTunes to work in ubuntu, because there is no real, suitable itunes replacement for ubuntu. I'm just so mad that apple isn't willing to port it's unix-based version of itunes for macs to unix-based Linux systems.

---

### Post by An85Zk9tc8rfjV8i on 2009-03-22
> **Depressed Man said:**
> those annoying phobos or itms links. So what you can do is..

1) Use PenguinTV. I know that one can handle iTunes links (says so at least)
2) Add podcasts in iTunes, export them into opml, import opml file into almost any music/podcast program (what I do).

find the rss feed (for example) :
[google : "this week in tech" filetype:xml]("http://www.google.com/search?hl=en&safe=off&as_qdr=all&num=100&q=%22this+week+in+tech%22+filetype%3Axml&aq=f")

[google : podcast]("http://www.google.com/search?as_epq=podcast&hl=en&num=100&safe=off)

where are the config files in ubuntu for Banshee ?

---

### Post by waster on 2009-04-06
> **Depressed Man said:**
> I don't know, but I say iTunes has the biggest podcast list probably (outside of 3rd party websites). But you get those annoying phobos or itms links. So what you can do is..

1) Use PenguinTV. I know that one can handle iTunes links (says so at least)
2) Add podcasts in iTunes, export them into opml, import opml file into almost any music/podcast program (what I do).

Yeah, how many music/media players do you know that take an OPML file?
Even if they did, my opml export is a mix of feeds of text, podcasts and video, which is bound to cause problems.

What I would like is an app, like those available on windows, which let you sync (not import/export - that is NOT syncing) feeds with online readers, such as Google Reader.

There is a 2007 patch for OPML support in Banshee, with no apparent development; rhythmbox is stuck in the 1990s. Amarok, Listen, etc.,etc. do not support OPML.

There is no straightforward way to get music from my feed collection to my music player, that I am aware of - please enlighten me if I am wrong!

---

### Post by bkadoctaj on 2010-03-03
> **woknam66 said:**
> Yeah, I've pretty much given up on this. I realized that what I really want is for iTunes to work in ubuntu, because there is no real, suitable itunes replacement for ubuntu. I'm just so mad that apple isn't willing to port it's unix-based version of itunes for macs to unix-based Linux systems.

Yep, unfortunately I've come to the same conclusion.  For now I'm keeping iTunes on a Mac OS X partition just for iPod work.  The truth of the matter is, I didn't need to purchase an iPod, but when I did, I wasn't using Linux and I didn't have the free software mindset.  As a result, I have a proprietary device (which overall is pretty good, aside from the relative incompatibility with Linux) and I will most likely continue to use iTunes to sync it for the time being.

There will come a day when Banshee (it seems to be the closest to full functionality from my perspective) will take care of videos and the "On-The-Go" playlist iPod features correctly.  When it does, you can bet I'll be back with Banshee.

Of course Apple has no interest in allowing Linux users to use iTunes - Linux users are hard to convert to Macintosh users, but Windows users are easy.  ;)

---

