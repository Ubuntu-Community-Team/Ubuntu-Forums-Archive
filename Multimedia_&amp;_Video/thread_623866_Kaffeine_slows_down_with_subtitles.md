---
title: "Kaffeine slows down with subtitles"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by filipe_aguiar on 2007-11-26
Hi, i have a problem with Kaffeine, it **slows down** when i'm using subtitles.

I have** Kubuntu Gutsy** installed, as well as all the codecs. The movie **plays smooth without subtitles**, but WITH them **slows every time that a subtitle appears**.

If someone could help me, i thanks in advise.

(sorry my poor english)

---

### Post by filipe_aguiar on 2007-11-26
I forgot, the other players do not slow down with subtitles, just Kaffeine.

(Off Topic - how can i delete a post?)

---

### Post by Zatta on 2008-05-06
Yes. It is because the xine engine is scaling the subtitles. Disable subtitle scaling and everything will go smoother: 

in kaffeine, go **Configurations->Xine Engine Parameters->Subtitles->Advanced->** uncheck "*use unscaled OSD if possible*".

If the size of the subtitles is too big or too small, pick another size in **Subtitles->Basic->** subtitle size.

Zatta.

---

