---
title: "Transcoding audio files and preserving audio tags."
date: 2010-10-13
forum: Multimedia Software
---

### Post by Racecar56 on 2010-10-13
There are about 500 MP3 audio files that I want to be transcoded into Ogg, but ffmpeg doesn't preserve audio tags. Is there some kind of trick to make ffmpeg preserve the audio tags, another program I should be using, or some command that can be run after the ffmpeg process is complete?

This conversion will be running on 2 CPU cores as a batch job with GNU parallel compiled from the GNU website, on Ubuntu 10.10. Thanks!

---

### Post by ron999 on 2010-10-13
> **Racecar56 said:**
>  Is there some kind of trick to make ffmpeg preserve the audio tags

Hi
With up-to-date versions of ffmpeg there is a 'map_meta_data' option.

Like this:-

```
ffmpeg -i input.mp3 -map_meta_data 0:0 -acodec libvorbis output.ogg

```

---

### Post by Racecar56 on 2010-10-14
> **ron999 said:**
> Hi
With up-to-date versions of ffmpeg there is a 'map_meta_data' option.

Like this:-

```
ffmpeg -i input.mp3 -map_meta_data 0:0 -acodec libvorbis output.ogg

```

It doesn't make any effect, strangely enough. I know I got the order of the options right according to the order you put in that code.

EDIT: The SVN version of ffmpeg does have an effect with that option, but it still doesn't preserve everything. Very close, though.

---

