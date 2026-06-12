---
title: "Goobox, Sound Juicer &amp; cd-extraction"
date: 2009-04-09
forum: Multimedia Software
---

### Post by orawax on 2009-04-09
Goobox doesn't give me the option to extract cd's into mp3 at all. I can only choose from ogg, flac and wav.

Sound Juicer does only 128 kbps CBR, and when I tried [these alternative parameters](http://ubuntuforums.org/showthread.php?t=1069647), it performed even worse (112 kbps).

I've got ubuntu-restricted-extras, lame and various gstreamer plugins installed.

What's the problem?

---

### Post by hansdown on 2009-04-09
Hi orawax.

To get VBR, you need to add a pipeline.

Stchman.com explains it quite well.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

His website is here.

[http://www.stchman.com/](http://www.stchman.com/)

---

### Post by orawax on 2009-04-09
Thanks,

I can't seem to get vbr working anyhow (at best I get something between 150-160kbps), but I guess I'm happy with 192kpbs cbr.

:guitar:

What about goobox? I like the interface but no clue about mp3.

---

### Post by logos34 on 2009-04-09
everytime I think I've got the gstreamer pipelines figured out in sound juicer, I go back and try them and find they don't work correctly, or the tags are wrong, etc.

Sound Juicer/Cd audio extractor is a P.O.S, in my considered opinion.  Just too much config and settings B.S. for mp3.

Try Grip, ABCDE or (on Wine) Exact Audio Copy (THE best ripper)

---

### Post by hansdown on 2009-04-09
This is an old thread, but it suggests a possible fix.

[http://swiss.ubuntuforums.org/showthread.php?t=295698&page=2](http://swiss.ubuntuforums.org/showthread.php?t=295698&page=2)

---

