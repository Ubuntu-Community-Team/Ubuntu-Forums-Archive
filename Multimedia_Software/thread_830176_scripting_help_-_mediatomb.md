---
title: "scripting help - mediatomb"
date: 2008-06-15
forum: Multimedia Software
---

### Post by graveson on 2008-06-15
hi,
can someone help me with this script. i cannot get it to work and it keeps on saying "line 14 no such file or directory"


#!/bin/bash

INPUT="$1"
OUTPUT="$2"
VIDEO_CODEC="mpeg2video"
VIDEO_BITRATE="4096k"
VIDEO_FRAMERATE="25"
AUDIO_CODEC="mp2"
AUDIO_BITRATE="192k"
AUDIO_SAMPLERATE="44100"
AUDIO_CHANNELS="2"
FORMAT="dvd"

exec /usr/bin/ffmpeg -i "${INPUT}" -vcodec ${VIDEO_CODEC} -b ${VIDEO_BITRATE} \
-r ${VIDEO_FRAMERATE} -acodec ${AUDIO_CODEC} -ab ${AUDIO_BITRATE} -ar ${AUDIO_SAMPLERATE} \
-ac ${AUDIO_CHANNELS} -f ${FORMAT} - > "${OUTPUT}" 2>/dev/null

---

### Post by jaton on 2008-06-15
I see that you script is the standard say from:
[http://gentoo-wiki.com/HOWTO_MediaTomb](http://gentoo-wiki.com/HOWTO_MediaTomb)

Are you sure that your ffmpeg is located in /usr/bin?

If it is in the right location try run it by hand, does it work?

---

### Post by graveson on 2008-06-15
excuse my stupidity, but i found the answer. i forgot to add the output file to the end of the command line. thanks anyway

---

