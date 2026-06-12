---
title: "MPlayer plugin problem"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by Drengur on 2006-11-11
I have installed MPlayer with the Ubuntu packaging system from the multiverse directory. Then I downloaded MPlayer plugin for Mozilla and installed it.

Firefox shows the plugin as installed but whenever I try to play a video on web-pages it asks for a plugin.

Any ideas?

Thanks upfront

---

### Post by Drengur on 2006-11-14
Anyone?

---

### Post by skymt on 2006-11-14
Many web videos these days (Youtube, Google Video, etc.) use Flash instead of a real embedded video. Follow the [directions for installing Flash](https://help.ubuntu.com/community/RestrictedFormats) (toward the bottom of the page) on the Ubuntu Wiki, and see if that solves your problem.

---

### Post by Drengur on 2006-11-15
Flash works just fine. This is not the problem.

With regards,
Drengur

---

### Post by skymt on 2006-11-15
Can you link to one of the videos? I'll see what plugin they want.

---

### Post by lchata on 2006-11-15
Strange, for me firefox plays, mozilla browser doesn't. I tried mozilla-mplayer3.17, mplayerplug-in-3.31 cvs compiled and mozilla-mplayer-3.31-3v1ubuntu2 from 
deb [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/) dapper 3v1n0; The latest version which you may want to try. Also the latest flash9 can be found there. Forefox played embeds with all of the above but not mozilla. You didn't say which versions and I don't have time to try figuring it out. You may want to look at your /etc and $Home dir to see if you have different versions or symlinks to a diff versions that are overriding what's in /usr/lib/firefox/pligins which is where I assume you put the newly installed plugins.
HTH.
Leonard Chatagnier

---

### Post by Drengur on 2006-11-15
Thanks for the effort.

This is actually for my father's computer as I am using FC5 and Windows 2000 on the side.

A typical video would be: [http://dagskra.ruv.is/streaming/sjonvarpid/?file=4285024](http://dagskra.ruv.is/streaming/sjonvarpid/?file=4285024) (don't worry totally safe for work)

I am not sure what version of everything I installed on his system, I will come back to you with all that.

Aside from this slight problem my father is very pleased and will not be returning to the awful world of Windows. I, myself have a bit of history with GNU/Linux as I have used severel different Red Hat systems (and FC) as well as Debian. I am not too keen on switching all the time but Ubuntu has got my attention, that's for sure.

---

### Post by skymt on 2006-11-15
It looks like it wants Windows Media Player 10. As far as I know, MPlayer only pretends to be WMP 9. You may have better luck with embedding mplayer using Mozplugger, but that gets very tricky very fast.

Another idea is to try installing Firefox and WMP using Wine. I have no idea whether that works, and I suspect it doesn't, so unless you find someone who did it successfully and has directions, it would be a big time sink.

---

### Post by medeski on 2006-11-15
I don't think WMP10 is a problem, because the video plays all right for me with the mplayer plugin.  That said, I'm actually running Debian and the plugin is from their repositories (testing.)  

Ichata's suggestions make sense.  Also, if you have multiple plugins installed you might try removing them and seeing if the mplayer plugin works without them.  At one point I had both it and the vlc plugin installed and neither of them would work.

---

### Post by medeski on 2006-11-15
One more thing - do you have the right codecs installed?
There's a similar thread going on at [http://ubuntuforums.org/showthread.php?t=300138](http://ubuntuforums.org/showthread.php?t=300138)

---

### Post by skymt on 2006-11-15
> **medeski said:**
> One more thing - do you have the right codecs installed?
There's a similar thread going on at [http://ubuntuforums.org/showthread.php?t=300138](http://ubuntuforums.org/showthread.php?t=300138)
Yes, installing win32codecs might help.

> **medeski said:**
> Also, if you have multiple plugins installed you might try removing them and seeing if the mplayer plugin works without them. At one point I had both it and the vlc plugin installed and neither of them would work.

This is unlikely to be the problem. Firefox goes through the list of plugins to find one that can handle the media format. If two plugins fight over the same format, they may not work, but you probably won't get the "missing plugin" error, since Firefox successfully found a plugin for the format.

---

### Post by Drengur on 2006-11-15
Thank you all very much for your suggestions. I will try as many of them as I can asap.

I do believe there are no other plugins installed, this is a new system and I don't recall installing anything else.

Regarding codecs I have no other codecs than those which came with the mplayer package found in the multiverse repositories, so that is a possibility. However, since Firefox asks for a plugin and the plugin doesn't ask for a codec, I thought not. But then again feedback has never been OSS's forté.

With regards,
Drengur

---

