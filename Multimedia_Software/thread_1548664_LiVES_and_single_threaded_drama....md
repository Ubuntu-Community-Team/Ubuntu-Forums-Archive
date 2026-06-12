---
title: "LiVES and single threaded drama..."
date: 2010-08-08
forum: Multimedia Software
---

### Post by toupeiro on 2010-08-08
So.. Lives COULD be one of the best video editing programs from a UI perspective, not just for linux, but in general but it has one apparent fallback in my eyes.  MANY portions of it are single-threaded...  I tried using different encoders through it but the result is the same.  I have a mkv screencast I created with ffmpeg (latest daily compile) and I used lives to blur a portion of the frames where identifying data was shown.  All I am trying to do is save my changes but I cannot do that in lives without re-encoding the whole entire file.  Fair enough, I have a core i7 940 @ 2.93 Ghz per core, it should give it a fair workout right?  wrong!

whenever LiVES tries to use the multi_encoder to re-encode an OGG/THEORA high quality file, it says it has to portionally resize it because it cannot handle 1680x1050 ... oh kay...  So I let it go ahead and start with gnome-system-monitor running and I see 1 out of 8 available cores pegged at 100% and the rest at idle.  REALLY?!?!?

So I pose this question.  Which other tool could I just as easily take a mkv file, blur a string of frames and save it in the same resolution and quality, without having to single thread my machine and my life to death?

ANY help at al is greatly appreciated!

Cheers!

-T.

---

