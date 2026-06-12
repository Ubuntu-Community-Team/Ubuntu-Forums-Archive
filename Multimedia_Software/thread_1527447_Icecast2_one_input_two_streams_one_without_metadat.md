---
title: "Icecast2 one input two streams one without metadata?"
date: 2010-07-09
forum: Multimedia Software
---

### Post by MikeUK on 2010-07-09
I&#8217;d like to understand what I need to do to create two streams from one input on Icecast2

I&#8217;m currently running ices0 to create and stream a playlist of mp3 files, it&#8217;s a basic setup up but it works and feeds Icecast2 which in turn streams out to XMMS, audacity and Rhythm box without issue. (I did it so long ago I&#8217;ve forgotten most of what I did)

I have recently added a Egreat M34A NMT to my setup, and have created (copied) an XSL file in the icecast web server section. The NMT can see the file, and buffer the stream., but I get no audio playback. I&#8217;m lead to believe that this is due to the metadata being streamed and that the Egreat NMT can&#8217;t handle the metadata (it does work with shoutcast streams)

I&#8217;d like to set up a second stream on the Icecast server but without the Metadata, see if this realy does solve the problem I&#8217;m almost sure that the command is <mp3-metadata-interval>0</mp3-metadata-interval> to shut down metadata transmission.

The sad part is I&#8217;m not sure how to create the second stream and then where to put the metadata shutdown command for just that stream?

Looking for help and advice

---

### Post by MikeUK on 2010-07-12
Partly solved.

The NMT doesn't show any metadata when its running and it takes a very long time to buffer, add in a long delay. if you don't wait long enough you assume it not working.
I walked away the othr day and didn't bother adjusting or resetting anything and after several minutes passed I had music.

I think my next steps will be to get the burst and buffer settings adjusted to suit the NMT

---

