---
title: "this website fails because of distribution, computer, browser, or something else?"
date: 2020-05-05
forum: Multimedia Software
---

### Post by anotherChris on 2020-05-05
I used to have Lubuntu 17.10 with Chrome, and with the old YouTube website, I could have several tabs with YouTube open at the same time.  Then, sometime within the last few months, YouTube re-tooled its website, and I stopped being able to have multiple tabs open--my computer would freeze up.  I thought the problem would be fixed when I installed Lubuntu 20.04 with Firefox, but it hasn't been.  YouTube website loads extremely slowly, and if I have more than one Firefox tab with YouTube, my computer becomes so slow its almost unresponsive.

It seems very unlikely the problem is with the latest Firefox.  I'm guessing the problem is probably with my computer (Dell Inspiron 1545), but I don't know if it could be with Lubuntu.

This is not a huge problem for me as I can watch YouTube on my Android tablet instead, but it's annoying when, for example, I am searching for Linux/Ubuntu solutions and want to look at YouTube videos showing how to do things in Linux/Ubuntu.

Anyone else have a similar problem or know what could be causing this in my case?

Thanks.  Sorry if I posted this in the wrong sub-forum.

---

### Post by lvm on 2020-05-06
Alas, youtube is a typical example of fat sluggish overadorned modern html5 website crawling with useless cpu-hogging scripts and thus requires a fast computer. The situation may be somewhat improved by using adblockers and browser addons for freezing background tabs but don't set your expectations too high. Note also that Firefox currently doesn't support hardware acceleration for html5 videos on linux while chromium does, so video playback in chromium may be not as hard on CPU.

---

### Post by guiverc on 2020-05-06
I use youtube in my QA-testing of Lubuntu (and other systems I test), though I only rarely use more than a single tab to that site (usually other tabs are to news sites usually heavy on text).

With 19.10 & 20.04 QA-testing all machines had 2GB or more of RAM, though I usually added ublock origin, privacy badger or ghostery (any one) so I was annoyed by adverts from youtube. I haven't done any *focal* testing since just before release (one test only so far with *groovy*), but I never taxed any test with multiple youtube tabs open (or if I did one in the background played music whilst the main tab was muted so only picture if the box didn't have any music on local drives).

On my main desktop here though, I have no problems at all. It's not a modern thing (*decade+ old c2q desktop*) but it has 8GB of ram which really helps.

---

### Post by Autodave on 2020-05-06
Install *uBlock *in Firefox and see how much that helps you.

---

### Post by anotherChris on 2020-05-11
> **lvm said:**
> Alas, youtube is a typical example of fat sluggish overadorned modern html5 website crawling with useless cpu-hogging scripts and thus requires a fast computer. The situation may be somewhat improved by using adblockers and browser addons for freezing background tabs but don't set your expectations too high. Note also that Firefox currently doesn't support hardware acceleration for html5 videos on linux while chromium does, so video playback in chromium may be not as hard on CPU.

Thanks.  My impression just from a gaphic design perspective is also that YouTube is bloated and tries to be too clever by half.  I used to use Chrome, but in 20.04 I was going to try to avoid it because of the SNAP issue, but maybe I will go back to it....   Is there another browser besides Chrome that is built on Chromium that you would recommend?  I am basically just interested in speed and not having my browser freeze up, and not so much in other functionality (like privacy).

---

### Post by anotherChris on 2020-05-11
> **Autodave said:**
> Install *uBlock *in Firefox and see how much that helps you.

Thank you.  I did install uBlock, and it does seem to help a bit.  With only 1 or 2 tabs of YouTube open, the YouTube website does seem to work much better and much faster.  However, with 6 tabs of YouTube open tonight, FireFox froze up for about 20-30 seconds (which is an eternity, as you know).

---

