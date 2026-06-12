---
title: "Ubuntu 14.04-avconv-drawtext."
date: 2014-04-19
forum: Multimedia Software
---

### Post by timsdeepsky on 2014-04-19
Hello,,
I have been reading other info on google and the forums and am still confused....
I use Ubuntu 12.04 with ffmpeg compiled from here [http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide]("http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide") with drawtext filter enabled....
When i install 14.04,,(this comes with libav i now believe),,is "drawtext" already there??
Or do i just change all my "ffmpeg" syntax in all my commands to "avconv"??..
Does avconv even support "drawtext"??..
Do i need to enable the "drawtext" filter in avconv??''

Seems to me i can still install ffmpeg fron here [http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide]("http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide"),,
with filters enabled,,and use ffmpeg..But then do i uninstall the libav from Ubuntu??..
Confusing is not even close to explaining it on this whole libav-ffmpeg fork....
Thanks for any info you can share with me....
Truly....

---

### Post by andrew.46 on 2014-04-19
> **timsdeepsky said:**
> Seems to me i can still install ffmpeg fron here [http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide]("http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide"),,
with filters enabled,,and use ffmpeg..But then do i uninstall the libav from Ubuntu??..

You should be able to use the version from the FFmpeg wiki and *not* uninstall the Ubuntu repository version.

> Confusing is not even close to explaining it on this whole libav-ffmpeg fork....

The fork has caused a very large amount of confusion amongst many users :(.

---

### Post by timsdeepsky on 2014-04-19
Thank you....
I will install ffmpeg from the wiki and move on....
Thanks again....

---

