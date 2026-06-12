---
title: "Soundjuicer/converter questions"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by element42 on 2007-05-03
Hi, I would really appreciate some answers to these questions:
1)How can I make SoundJuicer rip to FLAC level 8? (I guess I need to know the correct gstreamer pipeline, but I can't find any helpful info anywhere, and I've tried adding -8 in what seems to be the appropriate place but all that appears to do is make it rip at 8x speed!)
2)How can I make SoundConverter convert to mp3 with a CBR of 320kbps? (There is an option for 'very high' but that is only 256kbps...)
3)If I can't do the above, how can I make SoundJuicer rip to mp3 at 320kbps - ideally using LAME?

4)Perhaps - is there a way of ripping a CD simultaneously to both FLAC level 8 and mp3 320kbps in seperate folders with automatic tagging?

Thanks!

---

### Post by element42 on 2007-05-08
Okay, I've found a solution if anyone comes across this thread with a similar problem:
1)use abcde for ripping. it's in synaptic, and despite being command line, it's ace. does everything really nicely. You'll need to know how to configure the command line options for the encoder though!
2)use soundKonverter for converting. A bit like soundjuicer, but so much more useful.

---

### Post by stchman on 2007-05-08
> **element42 said:**
> Hi, I would really appreciate some answers to these questions:
1)How can I make SoundJuicer rip to FLAC level 8? (I guess I need to know the correct gstreamer pipeline, but I can't find any helpful info anywhere, and I've tried adding -8 in what seems to be the appropriate place but all that appears to do is make it rip at 8x speed!)
2)How can I make SoundConverter convert to mp3 with a CBR of 320kbps? (There is an option for 'very high' but that is only 256kbps...)
3)If I can't do the above, how can I make SoundJuicer rip to mp3 at 320kbps - ideally using LAME?

4)Perhaps - is there a way of ripping a CD simultaneously to both FLAC level 8 and mp3 320kbps in seperate folders with automatic tagging?

Thanks!

I have a procedure to download the codecs and configure Sound Juicer to rip your audio CDs to MP3s using the LAME encoder for VBR.

If you really want to you will need to get some new gstreamer pipelines.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

LAME is regarded as the best MP3 encoder out there.  VBR is the way to go.  During a quiet passage there is no need for super high bitrate.  I have pretty good ears and the LAME VBR encoding is darn near as good as FLAC.  As a matter of fact I can hardly tell a difference between the VBR MP3s from the original CD.  IMO 320Kbs is a waste of time.

Give it a try, you won't be disappointed.

---

