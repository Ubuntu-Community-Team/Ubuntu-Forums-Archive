---
title: "Thank u FFqueue"
date: 2016-11-28
forum: Multimedia Software
---

### Post by xinuzi on 2016-11-28
And thank you FFmpeg ([https://www.ffmpeg.org](https://www.ffmpeg.org)).

Encoding video with FFmpeg in the terminal is quite hard, so FFqueue ([http://ffqueue.bruchhaus.dk/](http://ffqueue.bruchhaus.dk/)) is a well made visual suit for this.

Easy installation on Ubuntu (64bits only). Unpack and just copy to personal space. Possibly shortcut to Desktop.

Read the Documentation or included html Help first.
Requires FFmpeg well set up and linked to.

All kinds of trouble with some other encoders on Ubuntu 16 for the moment.

E.g.:
- avidemux: hardly works anylonger.
- VLC: hangs sometimes when transcoding (but quite good for viewing and recording from composite/s-video sources).
- transmageddon: very slow, very limited settings.
- others: no cutting up in stream copy mode e.g.

---

### Post by TheFu on 2016-11-29
handbrake is another option. It is F/LOSS and in the repos.

Do you know of any Linux editors that accept EDL as inputs and will cut/split at those points easily?  I'm looking for a replacement to VideoRedo Suite. Currently using comskip to find all commercials, but need a GUI tool to validate/modify those cuts before doing the final saves and transcodes.

---

### Post by xinuzi on 2016-11-29
Personally had a problem with Handbrake not transcoding the audio of a specific video file.

The author of FFqueue advises to use a certain aac audio codec (the 'libvo_aacenc - Android VisualOn AAC codec' to be more precise) when converting to mp4.
That specific codec works very well in most cases indeed. 

Sth like FFqueue is also interesting for the included filters. E.g. the logo overlay or logo blur filter.

---

