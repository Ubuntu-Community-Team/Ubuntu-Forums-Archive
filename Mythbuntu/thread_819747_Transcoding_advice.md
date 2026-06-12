---
title: "Transcoding advice"
date: 2008-06-05
forum: Mythbuntu
---

### Post by bah1976 on 2008-06-05
I've read several different things about transcoding & HD content and such, and I'm hoping I can get a bit of real-world advice.  It's also possible that I haven't read the right info, and it already exists somewhere else.  If that's the case, a link is appreciated.

I have a combined be/fe with dual core AMD - 4400+ 2.3Gh, 2 GB ram, primarily capturing ATSC OTA with 2 Kworld 115 cards (plus CBS over QAM - until they switch freqs in Chicago in february).  I have a nvidia 6200le s-video out / MB audio line out to a magnavox A/V selector.  From there, I have it modulated on ch3 to the upstairs TV, and Svid + RCA audio to receiver and then finally Svid to TV.  The TV is not HD at this point (it's a 7-year old Sony wega), although the Svideo does look very nice.  I tried the modulated signal, and there is a definite difference in quality.  I've noticed just a hint of lag in viewing some of the shows, hence this post.  

That's the setup - now the questions - no comments from the peanut gallery on the rats nest of cables:
1) Is there anyway to tell the frontend to not send HD-quality signals out?  I don't need it to process to HD if I don't need to.  Is this where the OpenGL vs QT comes in?  All I need is s-video quality - nothing fancy.

2) If I can't tune down the front-end, what transcoding setup should I use if all I intend to view is s-video?  Space isn't an issue, I've got 1 TB to work with (minus about 50 GB of household samba-based data).  I just want no lag.

3) Long term, I plan to upgrade to HD and build a dedicated front-end for HD, but this back-end would continue to service the modulated signal to upstairs.  If I end up transcoding to help this back/frontend run better, does that mean that I'll lose my HD quality on a new frontend at that point?

If I'm way off base - please shove me back on.

Thanks in advance for your thoughts...

---

### Post by jlagrone on 2008-06-05
I don't know what you mean by lag.  If you noticed the show is slightly delayed from the same so on a different TV, this is perfectly normal.  Mythtv starts recording the program to a file and then starts playing that file after about 2 seconds.  If the playback is stuttering or choppy, post some more info and someone may be able to help.  Otherwise, answers to your questions

1.  If you're watching live TV, you are pretty much stuck with whatever the tuner card gives you.  Theoretically, you could transcode on the fly, but that would probably just slow it down even more (plus there's figuring out how to get it to work consistently)

2.  I autotranscode everything I record unless it is something special and I want to have a better quality.  The default settings it gives you for recordings work fairly well.  I usually use my "medium" transcoder setting for autotranscodes.  The settings follow (very likely to be the default settings):

Codec: MPEG-4
Bitrate: 1800
Max Quality: 2
Min Quality: 15
Max dif between frames: 3
Scale bitrate for framesize checked
High quality encoding checked
4MV checked

I also have a "lower quality" one that is the same except the bitrate is 1500.

3.  My transcoded programs still look good, but I don't get much in the way of HD content where I live so I can't say what if anything will be lost.  That being said, you can definitely still transcode HD and preserve most of the quality, you may just have to tinker a bit (I think I saw a chart with good settings somewhere on the mythtv wiki some time back, but I can't seem to find it at the moment)

---

