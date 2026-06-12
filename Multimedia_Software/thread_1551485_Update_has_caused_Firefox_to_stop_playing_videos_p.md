---
title: "Update has caused Firefox to stop playing videos properly."
date: 2010-08-12
forum: Multimedia Software
---

### Post by gencon on 2010-08-12
This morning Ubuntu (Lucid) had some updates available which I installed, without paying much attention to what they were.

I've now discovered in Firefox that some videos will not play at all, some play but the controls (like pause) do not function, and some play fine. BBC iPlayer videos will not play at all. Playing all videos in Firefox was fine before the update.

All videos on my hard disk appear to play fine in VLC and Totem, at least the ones I tested did, so it seems to be a problem with Firefox video playing only.

I am unsure how to find out what was updated this morning and so start diagnosing the problem, how do I do so?

Can someone please advise me what steps I should take to resolve this?

Many thanks all.

---

### Post by ebasa on 2010-08-12
I have a similar problem but with only one audio stream, I restored from my last backup and all is fine, but now afraid to install the 25 updates available.

---

### Post by gencon on 2010-08-13
> **gencon said:**
> This morning Ubuntu (Lucid) had some updates available which I installed, without paying much attention to what they were.
The packages which were upgraded are Flash related: flashplugin-installer and flashplugin-nonfree

Synaptic Package Manager's history shows the versions:

Commit Log for Thu Aug 12 10:19:22 2010
Upgraded the following packages:
flashplugin-installer (10.1.53.64ubuntu0.10.04.3) to 10.1.82.76ubuntu0.10.04.2
flashplugin-nonfree (10.1.53.64ubuntu0.10.04.3) to 10.1.82.76ubuntu0.10.04.2

Ever since then Flash has not worked properly in Firefox. BBC iPlayer no longer works at all.

Any ideas how to fix this?

Thanks.

---

### Post by travisf on 2010-08-13
I had a similar problem last week. Flash video very choppy or failing to play at all. Was using 64bit flash so went back to 32 bit version but that didn't fix the problem.

My problems seemed to start when the kernel was upgraded from 2.6.32-24.38 to 2.6.32-24.39 .

I fixed the problem by reinstalling the video card driver and now flash video works perfectly again. I use an ATI card with drivers from ATI, not the official distribution drivers.

---

### Post by sydbat on 2010-08-13
[Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/"). Brilliant Firefox Add-on from one of this communities best - lovinglinux!

---

### Post by travisf on 2010-08-13
To see what was updated start Synaptic Package Manager then use the File/History menu option.

(Ahh I see you did have a look at the history, but maybe see if there was also a recent kernel update)

I did use Flash-Aid to get back to the official 32bit version but that did not fix the problem playing video.

---

### Post by gencon on 2010-08-13
Thanks all.

Flash-Aid also did not solve my problem, Flash still does not work properly. (Yes I restarted Firefox after Flash-Aid had made it's changes, and I even re-booted).

Any other ideas?

---

### Post by travisf on 2010-08-13
If you are using proprietary video drivers I still suggest you try reinstalling them.

This fixed my problem with flash video due to a recent update.

---

### Post by gencon on 2010-08-14
I am not using proprietary video drivers.

---

### Post by gencon on 2010-08-14
Ok, in case anyone wants to know or has the same or a similar problem, I solved it by uninstalling flashplugin-installer and flashplugin-nonfree and then installing adobe-flashplugin (from the canonical repository).

I did this:

1. Totally quit Firefox.

2. sudo apt-get purge flashplugin-installer flashplugin-nonfree

3. sudo apt-get install adobe-flashplugin

That's all it took to get Flash working again !! :)

PS. I had already removed the Flash-Aid Firefox add-on.

---

