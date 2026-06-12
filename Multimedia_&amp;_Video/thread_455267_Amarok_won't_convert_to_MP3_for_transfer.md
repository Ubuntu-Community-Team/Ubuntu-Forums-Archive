---
title: "Amarok won't convert to MP3 for transfer"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by jabster on 2007-05-26
Hi.

I am running Feisty, fully updated, and am having a little problem with Amarok.

The media transfer finally works, and MP3 files transfer over just fine. But it will not convert flac or ogg to mp3 and transfer them. I get a "tracks not playable on media device."

I have amarok set to transfer MP3 directly, and to convert everything else to MP3. But it does not convert them.

My only workaround is to highlight files in my playlist, and use the soundkonverter plugin, saving the converted files onto the mp3 player that way.

I would like to use amarok directly for this.

Any ideas?

thanks,
john



p.s. I was having a problem earlier where soundkonverter would hang on the encoding process from FLAC, but after a brief conversation with a developer, I just had to delete the existing soundconverter log files. I don't see any log files for amarok specifically for converting tho.

---

### Post by Twinkel on 2007-08-11
I had a similar problem.  I fixed it by installing a transcoder script for amaroK (I use fftrans).  When the script is running, I can configure amaroK to automatically transcode "when necessary".

---

