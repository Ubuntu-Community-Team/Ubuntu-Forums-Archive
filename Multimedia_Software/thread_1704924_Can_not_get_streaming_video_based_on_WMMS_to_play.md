---
title: "Can not get streaming video based on WMMS to play"
date: 2011-03-11
forum: Multimedia Software
---

### Post by dBuster on 2011-03-11
Okay hopefully the title is enough to draw attention and hopefully get some guidance.  Seems that the forums have become so inundated with posts that many go unanswered.

I am working off of a recent clean install of Lucid (10.04.02) and I have relatives in Hawaii and this morning I tried to go to kitv.com to watch the live tsunami issues.  Only to learn that the live feeds would not work.

I have gone and installed the gstreamer plugins for mms as well as the vlc plugin for the same.  I have tried with both chrome and firefox and to no luck on getting the live feed to work.  I have no problems getting the videos to play from hulu or youtube so I am at a loss as to why I am having such issues.

I will post output of any commands that may be needed.

With FireFox I have installed mediaplayerconnectivity and have it setup for vlc to launch on any mms streams.  With the live feed I get the following error:

```
Your input can't be opened:
VLC is unable to open the MRL 'mms://a1064.l1289153063.c12891.g.lm.akamaistream.net/D/1064/12891/v0001/REFlector:53063'. Check the log for details.
```

No clue on how to check the log for details...

Thanks in advance.

---

### Post by ron999 on 2011-03-11
Hi
This link works for me with the live stream:-
[http://mfile.akamai.com/12891/live/reflector:53063.asx]("http://mfile.akamai.com/12891/live/reflector:53063.asx")

It plays in Firefox with **gecko-mediaplayer** plugin.

Also these commands work OK without using a browser:-
```
vlc mms://a1064.l1289153063.c12891.g.lm.akamaistream.net/D/1064/12891/v0001/reflector:53063
```

```
mplayer mms://a1064.l1289153063.c12891.g.lm.akamaistream.net/D/1064/12891/v0001/reflector:53063
```

```
smplayer mms://a1064.l1289153063.c12891.g.lm.akamaistream.net/D/1064/12891/v0001/reflector:53063
```

---

### Post by dBuster on 2011-04-06
Okay so the Tsunami is over with and I did not get to see any live feeds then...

So now I am trying to view live feeds of the Bald Eagle hatchings in Decorah IA and once again, I am unable to view live feeds.  I have no problems with streaming recorded video just something about getting a live feed to play.

What in the world?!  Do I need to go and run the 32/64 bit nonfree flash player?  I am running presently the latest 64 bit flash player obtained with flashaid in firefox...

[Decorah Eagles](http://www.ustream.tv/decoraheagles)

The attached screenshot shows what I see after waiting 5 minutes!  I have tried so much that I probably have hosed it all up but I hope not.  Would like to be able to view live streams!!

---

### Post by andrew.46 on 2011-04-07
Definitely a flash stream which plays fine here, screenshot attached. Can you play youtube videos and the like, or is it only this flash stream that is playing up?

---

