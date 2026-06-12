---
title: "what to do wiht audio out cables with two tuner cards"
date: 2008-12-08
forum: Mythbuntu
---

### Post by carpetfeller on 2008-12-08
This is my first experience with mythbuntu and with two tuner cards.  I have two cards that require (I think) an audio out cable to be plugged in to the sound card's line in jack.  With only one line in jack where do I plug the other tuner's audio out cable? Mic in or do I even need audio out to be plugged anywhere?

---

### Post by newlinux on 2008-12-08
what cards do you have? what kind of signal are you tuning? You may not need to use line out. Also, there may be a way to connect your cards internally to the sound card as well...

---

### Post by carpetfeller on 2008-12-08
One card is wintv go and the other is an ati tv wonder.  I will be capturing standard cable.

---

### Post by carpetfeller on 2008-12-08
I found this [here]("http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-Go"):

I have had no trouble with the WinTV (bt878) cards under Mythbuntu 8.04. I'm using a pair of them, and audio on both cards works fine without the need for pass-through cables. Live TV and recording works equally well in regards to picture quality and sound. The only real effort required to use these cards was the need to alter the brightness, hue, etc through mysql in order to eliminate washed-out looking picture quality. -- KAdams4458 20 May 2008 

But I also found this on the same page:

I have tried the WinTV Go card (with FM, without remote) and I managed getting it to work with MythTV. According to the first section on this page it should be possible to get this card running with sound without the cable that connects the line-out of the card with the line-in of the soundcard, but this was not possible with my tv-card/soundcard-combination. I have a MSI Media Live System that has an onboard sound and no matter how I tried in the last four days of hacking I coudn't manage to get sound without the cable. I think it depends on the WinTV Go card which is really old - I think I bought it back in 1999...

When finally using the cable I had sound - but the quality is very poor. It has also been poor on Windows back in early 2000 when I used it then. But now it's so poor that I decided to buy a Hauppauge PVR-250 card on ebay that encodes the sound with the video. Got it for roughly EUR 30. I hope the quality is better that way and I'll not have any more problems.

-- Johannes 21 January 2008


The audio on these cards will not work with mythtv or with tvtime. I have searched and tried a few workarounds. A pass through cable or the external sound jack is the only way to get audio, but this will not sync well for mythtv. Here is the bug report, [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789) It seems that kernels after 2.6.15 all have this issue. I would not try any bt87x card with mythtv until this bug is resolved. There are WinTV models that do work, WinTV-Go with FM is not one of them. Don't waste your time or money, especially when you can pick up a hauppauge pvr 150 for $40. ---mwcrowley 30 March 2008

---

### Post by newlinux on 2008-12-08
[http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-Go](http://www.mythtv.org/wiki/index.php/Hauppauge_WinTV-Go)
[http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder](http://www.mythtv.org/wiki/index.php/ATI_TV-Wonder)

The WinTV-Go wiki explicitely says it doesn't need a direct connection to sound card.

Edit: I see you found these...

---

### Post by carpetfeller on 2008-12-08
I guess if I read the whole page I would see that I don't need the cable with the proper drivers.

Thanks.

---

