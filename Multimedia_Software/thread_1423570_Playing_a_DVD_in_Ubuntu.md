---
title: "Playing a DVD in Ubuntu"
date: 2010-03-06
forum: Multimedia Software
---

### Post by sroberts82 on 2010-03-06
Ok, so I'm trying to do a pretty basic thing that I would like my computer to do. Play a DVD. It's proving difficult. Firstly, I have gone through all the normal (I say normal, but its not really) procedures of installing extra stuff that let me read encrypted DVDs. And I start up my DVD and watch it. For a little bit. Then comes the bit that breaks my movie enjoyment and ultimately makes me give up and wait until my main DVD player is working again. It stops. It fails. It gives me a cryptic error from whatever player I try. VLc, totem, mplayer, movie player. The lot, they dont want me to watch a film. I watch the first 10,15 minutes and then I get an error, cannot read from resource or some random C file is not interested in me finding out if the sundance kid succesfully robs a train. 

So, lets focus on one case. VLC. My distro is ubuntu 9.10 and I have installed all the libraries I need for decryption. The fact I can watch 10, 15 minutes proves this. Then I hit a point where it says "Could not read from resource" and the log look like this:
```

QPainter::begin: Paint device returned engine == 0, type: 1
[0x88aab60] main input error: ES_OUT_RESET_PCR called
[0x88aab60] main input error: ES_OUT_RESET_PCR called
[0x88aab60] main input error: ES_OUT_RESET_PCR called
[0x8a22248] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x8a19ca0] pulse audio output: No. of Audio Channels: 2
[0x88aab60] main input error: ES_OUT_RESET_PCR called
[0x892f678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x892f678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x88aab60] main input error: ES_OUT_RESET_PCR called
[0x892f678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x892f678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x88aab60] main input error: ES_OUT_RESET_PCR called
[0x892f678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x892f678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x88aab60] main input error: ES_OUT_RESET_PCR called
[0x892f678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
[0x892f678] libmpeg2 decoder error: DpbUnlinkPicture called on an invalid picture
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::setClipRegion: Painter not active
QPainter::setClipping: Painter not active, state will be reset by begin
QPainter::begin: Paint device returned engine == 0, type: 1
```

But here is the frustrating bit. If I restart the DVD and 30 seconds before these magic "lets break things" points, and fast forward by a minute, past the point of doom, everything is fine, for another 10 or 15 minutes. I am guessing the DVD is broken into various subsections and the player is not handling this. But surely there must be a player out there that can play a DVD from start to finish on ubuntu. So pleeeasseeeee help me, because I am coming close to leaving ubuntu because this is just one example of things that just dont work out of the box. Part of me hope the answer is as simple as "just do sudo apt-get install <stuff>" and part of me hopes not because that will just make me think why the f**k don't canonical think DVD playing is important enough to do this for me.

Anyway, problem described and rant over. Please help me if you can, I really want to see the end of Butch Cassidy and the sundance kid!!

Thanks
Stephen

---

### Post by RedSingularity on 2010-03-06
Does the DVD play fine in other OS's?

---

### Post by lidex on 2010-03-06
Try removing the ~/.dvdcss folder. It's hidden by default so in nautilus press ctrl+h to view if you don't see it.

---

### Post by balaknair on 2010-03-06
Sounds more like a DVD error(scratches/dirt on the disc) rather than a software error.
Have you tried playing the disc on other machines/OS? How about other DVDs on this computer, do they have the same problem?

And re the Canonical not shipping codecs and encrypted DVD support on the default CD, the reason is legal issues(libdvdcss2 could be seen as DRM circumvention, against US law). 
[http://en.wikipedia.org/wiki/Content-scrambling_system](http://en.wikipedia.org/wiki/Content-scrambling_system)

They can't distribute some of that stuff for free. If you buy a computer with Ubuntu preinstalled or if you buy an Ubuntu DVD from the stores, you'll find this stuff included, but not on the free CDs.

---

### Post by akand074 on 2010-03-06
Also do you have the medibuntu repositories enabled and installed the dvd descramblers? If not check out 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by sroberts82 on 2010-03-07
From the most annoying part of Ubuntu to the best! Thanks for all your responses and help guys, but I havent managed to resolve it. 

> Does the DVD play fine in other OS's?

Yep. In Windows it plays fine, in VLC (not media player). It is also fine in a standard DVD player. 

> Try removing the ~/.dvdcss folder. It's hidden by default so in nautilus press ctrl+h to view if you don't see it.

Tried that but didn't seem to affect anything.

> And re the Canonical not shipping codecs and encrypted DVD support on the default CD, the reason is...

Thanks for that, it is quite interesting. I guess I understand it now, but it doesn't make it any better :-)

> Also do you have the medibuntu repositories enabled and installed the dvd descramblers?

Well, I didn't so I followed all the instructions on that page and it installed a load of stuff. It didn't help solve the problem though. I just tried to run it in totem and VLC again.

Thanks again for all your help!

---

### Post by cowboy7305 on 2010-03-07
can you play any dvds bought or copied ones

---

