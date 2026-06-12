---
title: "Webtv - Needs WMAP to work"
date: 2010-03-07
forum: Multimedia Software
---

### Post by warelf on 2010-03-07
Hey, 

I'm trying to use a webtv subscribtion on ubuntu kermic, however it seems that that vlc dosnt support wmap yet, so i'm not getting any sounds on it. 

Does anyone have a clue on how to get this fixed, or if its even possible to get it fixed? I've tried searching guides for it without anyluck.

And when i'm trying to set it to use gmplayer or totem it dosn't work either, mplayer and totem dosnt get either picture or sound. 

Any help would be appriciated.

---

### Post by mc4man on 2010-03-07
Due to ubuntu's unwillingness to upgrade their ffmpeg libs or backport the ffmpeg wmapro patch to it's current ffmeg,  for vlc to support wmap you'll need to build your own.

(though lucid almost accepted the wmapro patch for ffmpeg - was removed/not included in last ffmpeg update - real  shame there

By far the best guide for that would be [found here]("http://ubuntuforums.org/showthread.php?t=1398119"), it is for the dev 1.1 version of vlc which for the most part works correctly but is subject to some breakages ect.

If desired the same method can be used to build a vlc 1.0.X release (1.0.5 atm), with just a few minor changes - if needed just ask

A self built or [decent ppa build of mplayer]("https://launchpad.net/~rvm/+archive/mplayer") would also work for wmap, you should be able to resolve any audio or video output issues quite easily
(smplayer is another frontend to ck. out

---

### Post by warelf on 2010-03-07
Thanks for some very good pointers mc4man. 

But unfortnaly it din't work out so good. Managed to compile everything, but when i tried and access the webtv now, i just get "VLC is unable to open the MRL" Check the log for details. So either picture and sound this time hehe. 

Can't find the log tho

---

### Post by mc4man on 2010-03-07
Sorry that I don't know a thing about Webtv, as far as the so called log

See here for a bit of explanation - 
[http://ubuntuforums.org/showthread.php?t=1331884](http://ubuntuforums.org/showthread.php?t=1331884)

(the 'log' is what you'll see when opening vlc from a terminal, you could start with just
vlc
or for more info (more is an understatement
```
vlc -vvv
```

(did you try a better mplayer (ppa or [build]("http://ubuntuforums.org/showthread.php?t=1305181")


Now if however this Webtv works, if it doesn't allow opening vlc or mplayer in a terminal then mention, there should be a way to create a log.

---

### Post by warelf on 2010-03-07
Finaly got it to work, found a alpha release of moonlight that managed to show it in silverlight instead.  Moonlight v2.99.0.3 managed to show it all it seems like. 

So that was the last piece of the puzzle on how to get rid of the virtualbox with windows on it :D

Thanks alot for your effort to help out :)

PS: looks like the quality is crap when using moonlight tho :(

---

### Post by mc4man on 2010-03-07
> PS: looks like the quality is crap when using moonlight tho

Noticed that while watching some Olympic video with moonlight, While it worked fine the difference in video quality between moonlight and silverlight was, sorry to say,  like night and day

(if you wish to pursue getting vlc or mplayer going for wmap then do see if you can produce some more verbose error messages..

---

