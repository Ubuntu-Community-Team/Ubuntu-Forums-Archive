---
title: "Add volume (gain) while downmixing AC3 to Stereo AAC?"
date: 2012-09-21
forum: Multimedia Software
---

### Post by MrsUser on 2012-09-21
I have a 6-channel AC3 which I converted/downmixed to 2-channel AAC. However, the volume is too low. And so I'd like to repeat the conversion with adding more volume (gain).

What do I have to add in order to apply some gain?

My command line is as follows:

```
avconv -i input.ac3 -f wav -ac 2 - | neroAacEnc -br 64000 -ignorelength -if - -of output.mp4
```It seems Nero can't do it. So it has to be applied on the fly on the WAV file.

EDIT:
I found the answer myself:
[https://wiki.archlinux.org/index.php/FFmpeg#Volume_gain](https://wiki.archlinux.org/index.php/FFmpeg#Volume_gain)

Example:
```
avconv -i input.ac3 -f wav -ac 2 -vol 1024 - | neroAacEnc -br 64000 -ignorelength -if - -of output.mp4
```

---

