---
title: "Videos can't play mp4 with libvorbis audio"
date: 2020-06-10
forum: Multimedia Software
---

### Post by stephenbbb on 2020-06-10
I am encoding the raw dv with:

```
ffmpeg -i dvgrab-025.dv -vcodec h264 -acodec libvorbis -ab 64k dvgrab-025.mp4
```

and the native Videos app in Ubuntu chokes and can't play the output. at the same time the SMPlayer or mpv Player can play it. Is there sth to setup for the default Videos app to play the mp4?

thanks everybody.

---

### Post by TheFu on 2020-06-11
i use this script:
$ more 2mkv-720
```
#!/bin/bash

FF_OPTS="-vcodec libx264 -crf 19 -vf scale=-1:720 -preset fast -strict experimental -c:a libvorbis -qscale:a 6"
for filename in "$@"; do

   ROOT=${filename/%.dv/}
   OUT="$ROOT.mkv"
   nice ffmpeg -y -i "$filename" $FF_OPTS  "$OUT"
done
```

Files can't have spaces in their names, but normal globbing works.  There's probably a better way to get the extension swapped.
I only use mpv or vlc to play videos.  mpv + youtube-dl are amazing. No commercials.

---

### Post by Yellow Pasque on 2020-06-11
> **stephenbbb said:**
> Is there something to setup for the default Videos app to play the mp4?
This should take care of any codecs you need for Videos/totem:
```
sudo apt-get install gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav
```

If you still have issues, describe what you mean by "chokes" and see if terminal produces meaningful error(s):
```
totem
```

---

### Post by SeijiSensei on 2020-06-11
I never use anything besides mpv and smplayer.  You should be able to make smplayer the default application for video extensions, too.  I've done that on Kubuntu, but I can't help with vanilla Ubuntu.

---

