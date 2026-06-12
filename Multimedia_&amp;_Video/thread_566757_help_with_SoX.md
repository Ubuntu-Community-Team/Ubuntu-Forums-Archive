---
title: "help with SoX"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by joereith on 2007-10-03
Re: 5.1 surround sound with sox
[quote=joereith]
Quote:
Originally Posted by taurus

well i have tried playing the left right center type files before they go through this command line and they are fine. So here is the command line that is making it wrong.


eval sox -V left.wav centre.wav right.wav left.wav right.wav lfe.wav -t raw - \| \
ffmpeg -y -f s16le -ar 48000 -ac 6 -i - -ab 384k \"$1.ac3\"

what is making the audio file play to fast? or what will make the audio slow down?

---

