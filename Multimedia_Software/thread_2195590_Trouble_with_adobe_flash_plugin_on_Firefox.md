---
title: "Trouble with adobe flash plugin on Firefox"
date: 2013-12-25
forum: Multimedia Software
---

### Post by rdh61 on 2013-12-25
Lubuntu 13.10, trouble with adobe flash plugin on Firefox version 26.0.

Trying to watch the videos on this page: [http://learnfluteonline.com/flute-lesson-module-2/](http://learnfluteonline.com/flute-lesson-module-2/)

The videos play (sort of) but are unwatchable because the graphics appear extremely distorted.

I have the latest version of adobe flash player installed with Synaptic Package Manager. However, when I click on tools -> add-ons -> plugins -> check to see if your plugins are up to date, I am told shockwave flash should be updated as it is "vulnerable". I click "update now" and am taken to the adobe download page. I click "download now" and nothing happens. (I have the latest icedtea plugin installed, too).

Is this a problem with flash or is it a problem with my not having activated plugins or what (add-ons manager gives them all as "always activate") or is it just that Firefox sucks?

Would appreciate any advice. 

Many thanks.

---

### Post by vasa1 on 2013-12-25
> **rdh61 said:**
> ... **is it just that Firefox sucks**?

Would appreciate any advice. 
...
My advice is to leave out stuff like that. Instead of getting suggestions on how to fix your problem, you'll get a lot of "other" advice.

---

### Post by monkeybrain20122 on 2013-12-25
Works for me totally.

Interesting thing is, it plays in html5 player in Chrome whereas it requires flash to play in FF (i have gstreamer enabled in FF).

---

### Post by rdh61 on 2013-12-26
> **vasa1 said:**
> My advice is to leave out stuff like that. Instead of getting suggestions on how to fix your problem, you'll get a lot of "other" advice.

Yeah, sorry, just frustration. Please disregard that remark. Anybody got any further advice?

Many thanks.

---

### Post by rdh61 on 2013-12-26
Update: uninstalled and reinstalled adobe-flashplugin, and activated in Firefox browser. Same result. 

Also, this card comes out distorted and unviewable, not only in Firefox but also in Chromium: [http://www.jacquielawson.com/viewcard.asp?code=4496819117646&source=jl999&utm_medium=internal_email&utm_source=pickup&utm_campaign=receivercontent](http://www.jacquielawson.com/viewcard.asp?code=4496819117646&source=jl999&utm_medium=internal_email&utm_source=pickup&utm_campaign=receivercontent)

(In Chromium though I can view the videos, even though a little off colour).

---

### Post by rdh61 on 2013-12-26
Further update. It's not just Firefox but Chromium, too. I've tried to look at other videos using chromium and they come out distorted, too. (But funnily, not the one which was the motivation for this thread in the first place). Am I the only one with this problem?

---

### Post by rdh61 on 2013-12-27
I've done some experimentation and it seems that playing media on browsers in Lubuntu is fraught with difficulty. I have tried 3 browsers (Firefox, Chromium, Chrome) using the default media player plugin (Gecko) or Adobe flash plugin or Gnash browser plugin.
I tried with two different sites offering online music lessons on video:
(1) [http://www.freeguitarvideos.com/mandolin/lessons/getting-started.html](http://www.freeguitarvideos.com/mandolin/lessons/getting-started.html)
(2) [http://learnfluteonline.com/flute-lesson-module-2/](http://learnfluteonline.com/flute-lesson-module-2/)
On the (2) I could test only the two flash options, as they seem to be used by default on this site (at least with FF) with no option to use the media player.


Here are my results:

Firefox:
Adobe Flash does not work at all on either site.
Gnash works on only one of the above sites (1), but the controls overlay the picture.
Gecko works.

Chromium:
Adobe Flash works only on (2).
Gnash works on both sites but on (1) the controls overlay the picture.
Gecko does not work.

Chrome:
Adobe Flash works well on both sites.
Gnash works on both sites but on (1) the controls overlay the picture.
Gecko does not work (sound but no picture).

Is no one interested in this issue?

In particular, I should be interested in anybody's ideas as to why things should work perfectly for one user (see monkeybrain20122 above) but not for another, me for example.

monkeybrain20122 mentioned that they had gstreamer enabled in Firefox. I see in Synaptic that I have gstreamer installed, but it is not listed in the Add-ons manager in Firefox. How would I enable it?

You can see that I really have no idea. Please help.

---

### Post by monkeybrain20122 on 2013-12-27
> **rdh61 said:**
> 
monkeybrain20122 mentioned that they had gstreamer enabled in Firefox. I see in Synaptic that I have gstreamer installed, but it is not listed in the Add-ons manager in Firefox. How would I enable it?

.

Both your links play perfectly in Firefox with flash, not sure how to use gecko to play  them. BTW, it can cause a problem if you have both flash and gnash  installed.

Gstreamer plugin probably has no relevance to your problem. Certain web sites offer html5 alternative to flash (e.g Vimeo, dailymotion(?) and soundcloud) but they use h264 so firefox could not play those streams in html5 (so must use flash) This has changed since FF24/25. FF now can play those contents in html5 if gstreamer is enabled. I mentioned that because Chrome didn't use flash at all to play your flute link, it was played in html5 by default. But in FF there is no html5 option on that site and when I disabled flash it simply wouldn't play, even though I have gstreamer enabled. 

To enable gstreamer in FF enter about:config in the url bar, then search for gstreamer and set 'media.gstreamer.enabled' to be true.

---

### Post by rdh61 on 2013-12-28
Thanks. I didn't have both flash and gnash installed - I made sure I installed / unistalled so only one was available (and also enabled in the browsers) at a time.

So, is there any way one could find clues as to why they both play perfectly on your system and not on mine?

---

### Post by monkeybrain20122 on 2013-12-28
I have no idea why they work on mine but not yours. I have not changed anything, eveything re flash is just default. It may be your graphic driver, or maybe some settings in flash are corrupted. Try remove the hidden folder .adobe and see if it helps. Another thing is that if you have enabled hardware acceleration try disable it (look for the file /etc/adobe/mms.cfg, it shouldn't be there by default but you might have created one in case you tried to use hardware acceleration in the past)

---

### Post by rdh61 on 2013-12-28
Removing .adobe didn't help. There is no /etc/adobe directory. Thanks anyway.

---

### Post by monkeybrain20122 on 2013-12-28
Well what is your graphic card? Which driver do you use?

---

### Post by rdh61 on 2013-12-28
Graphics card: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
Driver: i915

---

### Post by monkeybrain20122 on 2013-12-28
Sorry, everything seems to be in order I am not sure why it doesn't work for you.

---

### Post by monkeybrain20122 on 2013-12-28
Ok found this [http://askubuntu.com/questions/335124/flash-player-a-big-bug](http://askubuntu.com/questions/335124/flash-player-a-big-bug) 
Sounds a bit like your problem. Maybe updating your graphic driver would work?

Instead of downloading the deb you can simply add the xorg-dger ppa and upgrade
[https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=saucy](https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=saucy)
But beware that there is always a bit of risk upgrading the graphic driver, better backup your data and install ppa-purge just in case.. And disable the ppa if it works, you don't want to get regular updates from the edgers.

---

### Post by kalehrl on 2013-12-29
Create a file xorg.conf and put it in /etc/X11 folder.
Paste these lines in the file:
```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"
   Option      "AccelMethod"  "uxa"
EndSection
```
Reboot.

---

### Post by rdh61 on 2013-12-29
Big thanks to both of you. Yes, monkeybrain20122, judging from the screenshot in the first link you provided, that is exactly my problem.

I actually followed Kalehrl's advice first as it seemed the simplest and safest thing to try first, and it has worked. So, problem solved.

But before marking this as solved, for my own interest, how does what kalehrl suggested (creating an xorg.conf file) relate to the advice to update my graphics driver, suggested in monkerbrain20122's link?

---

### Post by kalehrl on 2013-12-30
In the latest kernels, they have started using SNA intel acceleration method instead of UXA which was used earlier.
This is better for the newer intel hardware but it creates problems on old intel graphics cards:
[https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006000.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006000.html)

---

### Post by rdh61 on 2014-01-02
I get it. Thanks again.

---

