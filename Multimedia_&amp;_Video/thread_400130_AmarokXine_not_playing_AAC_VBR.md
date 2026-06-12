---
title: "Amarok/Xine not playing AAC VBR?"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by thegestetner on 2007-04-03
Hi all,

Thanks to my iTunes-using past, I have several gigs worth of VBR AAC files (~192k.)
However, most of them don't work under Amarok/Xine on Kubuntu - I get a "no suitable demux plugin" error, which leads me to think that they aren't being recognized as valid AAC files.

Any suggestions?

---

### Post by crispy_420 on 2007-04-03
The are most liking the victim of DRM. Their two types of AAC, open and protected. Apple only sells protected (some new ones are not though, new as of this week). They are seen as extensions of MP4 and M4A.

[Here]("http://en.wikipedia.org/wiki/MP4") is a little info.

---

### Post by thegestetner on 2007-04-04
I appreciate your reply, but sadly these are unprotected files (*.m4a) that I all ripped from my own CDs. The only different between a regular AAC file is that they're variable bitrate instead of the constant bitrate (iTunes Store songs, iTunes default, etc.).

---

### Post by st14n on 2007-07-19
Did you find an answer to this? I also have problems playing VBR AAC in Amarok (ripped with Sound Juicer). However, I don't get an error message, but the sound is extremely "choppy". (Haven't tried CBR yet, so don't know if that works.)

---

### Post by manimaul on 2007-10-22
The answer to your question is different depending on your Ubuntu version and the program your using to play the aac file with.

Running Ubuntu 7.10 you need:

libxine1-plugins (If your using Amarok)
OR
(1 of the following... not sure which one specifically for AAC.)
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse (if your using Rhythmbox)

Before Ubuntu 7.10 you would have needed libxine-extracodecs for Amarok and some of the same ugly and bad plugins for gstreamer.  

Note: "Ugly" and "Bad" refer more to the licensing situation and not necessarily the quality of the packages.  In general, I install all of the libxine gstreamer plugins and everything plays.

Hope this helps

---

