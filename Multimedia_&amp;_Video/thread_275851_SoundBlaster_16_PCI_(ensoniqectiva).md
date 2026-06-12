---
title: "SoundBlaster 16 PCI (ensoniq/ectiva)"
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by quiv on 2006-10-12
Hi. I hate posting this question, because I have read every post I can find and none of them address my issue, so i'm certain that i'm either insane or there is no solution. 

I had an old Diamond Multimedia Monster Sound card with Aureal chipset when I first installed Breezy. It never sounded right (tinny, staticky) even after upgrading to Dapper, so I finally wrote it off as being fried and decided to spend the $20 to get another card. I picked up an OEM Creative Soundblaster 16 PCI card, tossed it in, Ubuntu detected it as an Ensoniq Ectiva and the snd-ens1371 drivers appear to have been loaded. From my searching I beleive this is an accurate detection. Well, I can't get a peep out of this card. i've set everything in Alsamixer, nothing is muted. modprobe snd-ens1371 does not return an error. I tried to unload it, and Ubuntu told me that it was in use. 

All of the topics i find regarding the es1371 seem to indicate people are having trouble getting the drivers loaded... mine appear to have loaded fine, so I am not sure what to try next. I have read the comprehensive troubleshooting guide with no luck as well. 

any ideas?

---

### Post by encompass on 2006-10-12
Does it act like it is playing sounds?  You can adjust the sound volume... hmm
well, I would first chack to see if the sound is not comming out of the different jack.  I had that with my cheap sound card, 20$, from walmart.
Play a song and then turn everything down then up and then check each jack and see if sound comes out.  Are there any integrated cards, or webcams or devices with sound in or out?

---

### Post by quiv on 2006-10-12
Hi, thx for the response. Yes, it "acts like it is playing sounds",   as far as I can tell anyways... XMMS shows the moving bars (I forget what the right word is for this). This sound card has three outputs; one pink, one green and one blue. I started playing music, then switched the plug into each of the three outputs, but nothing.

> Are there any integrated cards, or webcams or devices with sound in or out?
Not sure what you mean by this... no webcams, no other devices with sound in or out...

---

### Post by encompass on 2006-10-13
have you checked this link?
Helps alot of people...
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Don't know how else to help you... but lord raiden seems to know his stuff.

---

