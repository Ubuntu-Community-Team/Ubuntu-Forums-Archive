---
title: "FFmpeg sound codec problem"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by mitsuo on 2006-12-14
It's been a couple of days already, that mplayer has stopped playing audio properly with the FFmpeg audio codec, instead of the audio output I am supposed to get, I get some noise.. but not really static,, it's hard to describe..
Had anyone encountered this problem and know the way to fix it?

---

### Post by Nrvnqsr on 2006-12-17
by chance its like a warping churping sound? is it a mpeg2, 3 audio format?
try this Preference>Codecs & demuxers>Audio codec family
select "libmad mpeg audio decoder"

try that lets see how it goes

---

