---
title: "Fullscreen video streams lag/skip one both computers, what am I doing wrong?"
date: 2009-05-30
forum: Multimedia Software
---

### Post by tdietz87 on 2009-05-30
Okay, so I have installed 9.04 on two different laptops now and I've noticed on both laptops that when I attempt to watch anything I stream in Fullscreen it will skip and lag, but as soon as I escape fullscreen playback is normal.

I was wondering if this is a common problem since I've noticed it on both laptops?  is there a codec I am missing?  This problem seems to be true on youtube, hulu, etc.

any ideas?

I have a feeling my gfx card is working fine because my desktop is full of animation and extras that I feel wouldnt run properly if my gfx card wasn't working.

---

### Post by tdietz87 on 2009-05-31
bump

---

### Post by vapblack on 2009-06-03
Well, I can't really help you with all the other video sites, but to get YT to run perfectly, do the following:

download and install the addon ["Greasemonkey"]("https://addons.mozilla.org/en-US/firefox/addon/748")

Next get the script ['youtube without flash']("http://userscripts.org/scripts/show/41722")

what that does is makes it so you can run the mp4 versions of videos, rather than the flv versions. When you go into fullscreen, you are actually going in fullscreen in movie player. but it looks exactly the same as if you were doing it with the flash plugin. The videos look even better than if you ran it in windows.

---

### Post by caeroe on 2009-06-03
I have yet to get acceptable full screen performance for Hulu or any full screen flash video.  The workaround with Greasemonkey is good if I download them directly, but that's just for Youtube.

For Hulu I use pop-out and resize the window a little.  I tried asking for a better solution in IRC chat and one response was "use Windows".  

So disappointing.

---

### Post by vapblack on 2009-06-04
you dont have to download it. it just plays. you can let it automatically play as well, it'll be the same as the regular flash plugin. 

I can't get the other flash players to work either tho.

---

### Post by ScrantonSka on 2009-06-08
bump
same problem

---

### Post by caeroe on 2009-06-08
You guys have Nvidia cards?  Because my older notebook runs flash fullscreen just fine, with an ATI 64mb card in it.

Both machines run 9.04 64bit, Firefox, the flash drivers from Synaptic, and medium desktop effects.  The desktop has a Nvidia 8800GT 512mb card, as well as being a much more powerful rig.

---

### Post by vapblack on 2009-06-08
> **caeroe said:**
> You guys have Nvidia cards?  Because my older notebook runs flash fullscreen just fine, with an ATI 64mb card in it.

Both machines run 9.04 64bit, Firefox, the flash drivers from Synaptic, and medium desktop effects.  The desktop has a Nvidia 8800GT 512mb card, as well as being a much more powerful rig.

I have an nvidia card. Dunno why it does this..

---

### Post by Saganite on 2009-06-09
Same problem win Jaunty x64.  Work around is to right click on the vid while playing and set the quality setting to low.  Loose a bit of quality, but the jerky playback goes away.   However while messing around with this I did some fiddling, using the normal flash via synaptic etc and got REALLY jerky performance.  I removed all that and reinstall flash 10 with the special script for x64 and it's working again..still slow in high quality (regardless of rez or SD/HD) but low quality works well.

---

### Post by cham93086 on 2009-07-02
I've had a similar problem, constant jerky motion, or even only 1-2 FPS, but, perfect sound.  I tried several combinations of unintalling and reinstalling.  It turns out I solved my problem by installing the non-free flash, then removing the "swfdec-mozilla" package.  I don't know how or why it worked, but, another site said something about it getting higher priotiry than the non-free package.  Good luck

---

