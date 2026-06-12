---
title: "difference between players? (gstreamer/xine/mplayer/vlc/audacious/etc.)"
date: 2010-05-07
forum: Multimedia Software
---

### Post by agnes on 2010-05-07
I was wondering, if anyone could tell me the difference in concept between these, or point me to a useful link explaining that.
I mean the theoretical engine/plugin stuff. I know it vaguely but am not sure.

As far as I know vlc and audacious are apps which use their own video and sound 'playback engines'; while xine and mplayer basically *are* 'playback engines', and gstreamer is in some way a collection of playback plugins... right? Or not? 

I was also, actually mainly, wondering: do they overlap in playback functionality? For example do mplayer and (for example) totem-gstreamer sometimes use the same codecs/libs (for some formats)? Like ffmpeg?

---

### Post by andrew.46 on 2010-05-07
Hi agnes,

I can start the ball rolling by speaking about MPlayer, I am sure that others will step in with the other players you mention. At the heart of MPlayer is [FFmpeg's libavcodec]("http://en.wikipedia.org/wiki/Libavcodec") and away from Ubuntu MPlayer ships with its own version of this library of codecs. Under the default installation of MPlayer under Ubuntu there is a 'shared' version of libavcodec that has been stripped of various codecs that do no agree with the Ubuntu ethos. MPlayer also has the ability to use some windows codecs which under Ubuntu can be downloaded from Medibuntu, when it is up :). There is a great deal more to the MPlayer story but that is the basics...

All the best,

Andrew

---

### Post by agnes on 2010-05-10
Thanks for your reply.
I saw libavcodec is part of ffmpeg, so I read about that too... I have a better overview now.
Also, if I have correctly understood GStreamer is just a framework/API that mainly uses pre-existent codecs, so it's inherently not really different.

Reason I asked is because sometimes people experience (or say) their video or audio is better with one program than with another... got me interested.
But in the case that a codec of libavcodec is used by both xine (uses libavcodec too) and mplayer, on the same file, and you have xine and mplayer use the same video output mechanism - there should not be any difference, right? And that would be in most of the cases. So I guess between xine and mplayer it are e.g. the w32 codecs for wmv files that can make a difference (they do that different, maybe not under Ubuntu but they can).

I like mplayer most myself, for playing, it plays many formats.. but also because of the nice subtitle support, video output method selection, equalizer etc. :)

---

### Post by andrew.46 on 2010-05-10
Hi agnes,

Mind you the windows codecs are becoming less necessary these days as libavcodec can often give equivalent or better performance. This of course presupposes the usage of a recent and uncrippled libavcodec which can be a problem in many distros, not just Ubuntu...

As to which media player gives better performance, well in Australia we often talk about the difference between Ford and Holden cars and people will argue endlessly on the subject. It is a little like that with media players and playback under Linux I guess, except that obviously the best and most flexible player is MPlayer by a long shot :).


Andrew

---

### Post by Slug71 on 2010-09-21
I know this thread is a little old but i too have just been looking into this.
Can Mplayer effectively replace Gstreamer?

---

