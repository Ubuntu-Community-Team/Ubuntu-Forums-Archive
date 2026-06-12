---
title: "mythweb / mythffmpeg help"
date: 2014-05-28
forum: Mythbuntu
---

### Post by whosmatt on 2014-05-28
Pardon if this has been answered, but my search didn't turn up anything pertinent.

I recently upgraded from 12.04 to 14.04, with the usual pains.  I've gotten most of them sorted out now, but one little issue with mythweb and flv playback of recording.  When I first got mythweb working after the upgrade, I was delighted to see multi-threaded transcoding (with mythffmpeg) when playing back recordings in the browser; this meant that for the first time my system was fast enough to transcode HD recordings in real time.  I tried changing the settings to see how much better I could make the quality, and once I did that, mythweb won't play flash anymore; I am unable to check the box for "Enable Video Playback" due to "ffmpeg with MP3 support not detected."

Any ideas?  I have tried reconfiguring mythweb with dpkg-reconfigure and no change.

M

---

### Post by whosmatt on 2014-05-28
Ok, I fixed this temporarily by editing lines 27 and 28 of /usr/share/mythtv/mythweb/modules/tmpl/default/set_flvplayer.php.

I simply changed references to "ffmpeg" to "mythffmpeg" and we're back in business.

---

