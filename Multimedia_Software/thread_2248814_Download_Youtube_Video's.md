---
title: "Download Youtube Video's"
date: 2014-10-17
forum: Multimedia Software
---

### Post by Ritchiejoe8 on 2014-10-17
Is it possible to download youtube video's as MP4 or convert them to MP3 on Ubuntu 14.04? I have had a look for an alternative to Free studio which I previously used on windows but the only tutorial I could find was in german.

Danke

---

### Post by slickymaster on 2014-10-17
You can convert MP4 to MP3 using **ffmpeg**.
```
ffmpeg -i filename.mp4 filename.mp3
```

---

### Post by ajgreeny on 2014-10-17
If you want a gui try winff

---

### Post by andrew.46 on 2014-10-17
Well you should not actually download youtube videos at all as this violates their Terms of Service, also the Forums moderators will normally weigh in on this issue fairly quickly. So I can't help you with this one...

However there are other sites that you can look at that do not have this restriction, the better of them being TED talks which uses a [Creative Commons license]("http://creativecommons.org/licenses/by-nc-nd/3.0/"). This allows you to share the material with some restrictions.  On this site youtube-dl works well and for an example try this talk on sleep:

```

youtube-dl 'http://www.ted.com/talks/jeff_iliff_one_more_reason_to_get_a_good_night_s_sleep' \
           --extract-audio --audio-format mp3 --audio-quality 4 --keep-video \
           --prefer-ffmpeg --output "%(title)s.%(ext)s" --no-part

```

This* legally *downloads the video and then uses FFmpeg to convert to mp3 audio while keeping the original video. If you have avconv use *--prefer-avconv* instead of *--prefer-ffmpeg*. If you get some errors run the following:

```

youtube-dl --update

```

and this should get you the latest version. Can I say that the TED talks are a much more valuable resource than 90% of the material on youtube????

---

### Post by matt_symes on 2014-10-17
> **andrew.46 said:**
> Can I say that the TED talks are a much more valuable resource than 90% of the material on youtube????

Yep !

---

### Post by barryk on 2015-01-01
Give <snip> a try

---

### Post by vasa1 on 2015-01-01
> **barryk said:**
> Give <snip> a try
Thanks, but I won't ;)

---

### Post by lisati on 2015-01-01
> **andrew.46 said:**
> Well you should not actually download youtube videos at all as this violates their Terms of Service, also the Forums moderators will normally weigh in on this issue fairly quickly. So I can't help you with this one...

Good call.

Please read [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

Thread closed.

---

