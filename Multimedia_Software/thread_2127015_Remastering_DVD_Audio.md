---
title: "Remastering DVD Audio"
date: 2013-03-18
forum: Multimedia Software
---

### Post by OmahaVike on 2013-03-18
Hi there,

I sincerely appreciate any and all assistance in advance.

I'm trying to remaster an old DVD I made of a live performance.  So, I cat all the VOB files into one something akin to:

```
cat VOB_01_1.vob VOB_01_2.vob VOB_01_3.vob > master.vob
```

then I try to extract the audio from it using mplayer

```
mplayer master.vob -aid 128 -dumpaudio -dumpfile audio_original.ac3
```

At this point, I pull up duration of both files to see where I'm at:

```

mediainfo -f master.vob
----
duration:  02:12:11.357

```

```

mediainfo -f audio_original.ac3
-----
duration:  02:12:11.136

```

Hmmm...  that's really wierd.

So, I pull up the master.vob into cinelerra (because i need to trim and add in the remastered audio at a later time).  Simply playing the master.vob in the compositor screen, the video and audio are WAY out of sync.  But if I pull up this VOB in VLC, the video is in total sync.

Here are my questions:

1)  Can cinelerra handle this type of job?  If so, how can I get the audio and video to sync correctly?  When I've tried it several times before and rendered the video, audio was still way off, so I'm guessing its not just the compositor.

2)  Is there a more reliable tool where I can mux the raw video from the VOB and a remastered audio file that I've conjured up?  I would want to exclude the audio embedded in the VOB, and rely upon the stream I extracted using the mplayer command above.

3)  Am I going about this all wrong?

Again, thanks in advance for any and all help!

---

### Post by veroslav on 2013-03-19
For 2), you might be able to achieve that by using mplex. Something like:

```
mplex -f8 -o output.mpg input.m2v input.ac3
```

---

