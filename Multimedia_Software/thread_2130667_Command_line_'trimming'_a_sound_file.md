---
title: "Command line 'trimming' a sound file?"
date: 2013-03-30
forum: Multimedia Software
---

### Post by jimford on 2013-03-30
I have lots of audio podcasts that all have the same introduction, which is tiresome to listen to each time. Is there a way I can delete the first 30 seconds (say) on each file using a command line with a regex input? I can do it on individual files with audacity or other GUI editor, but with many files it would be very tedious.

I'd welcome suggestions, please.

Jim

---

### Post by evilsoup on 2013-03-30
There are a number of tools, though I would use ffmpeg.

```

ffmpeg -i input.mp3 -ss 30 -c copy output.mp3
## or (faster, but less accurate):
ffmpeg -ss 30 -i input.mp3 -c copy output.mp3
## or (lossy re-encode, takes longer, but the most accurate splitting):
ffmpeg -i input.mp3 -ss 30 -c libmp3lame -q:a 3 output.mp3

```

avconv, which is in the repositories, uses the same options. This does require creating a separate file for the output - but you can always delete the original when you're done, and that's pretty trivial to work into a script.

To do every mp3 file in a directory:

```

for f in *.mp3; do ffmpeg -i "$f" -ss 30 -c copy "trim-$f"; done
##  for recursiveness, use find:
find . -type f -name "*.mp3" -exec ffmpeg -i '{}' -ss 30 -c copy trim-'{}' \;

```

---

### Post by jimford on 2013-03-30
Thanks a lot 'evilsoup' - it looks like just the thing I need. I'll be off now to give it a try.
.
.
Yup - tried it and it worked a treat. (I used avconf because I got 'spooked' by the warning that ffmpeg is now deprecated!)

Thanks again 'evilsoup'.

---

### Post by tgalati4 on 2013-03-30
Don't forget *sox*, the swiss army knife of audio files.

```
sudo apt-get install sox
man sox
```

---

### Post by andrew.46 on 2013-03-30
> **jimford said:**
>  (I used avconf because I got 'spooked' by the warning that ffmpeg is now deprecated!)

FFmpeg is most definitely not deprecated, that misleading message is part of a nasty war between the avconv developers and the FFmpeg project.

---

