---
title: "Trouble converting MKV to AVI - Mencoder"
date: 2011-08-29
forum: Multimedia Software
---

### Post by sparker1 on 2011-08-29
I have been trying all day to convert an MKV to an AVI (xvid) so that it will play on a standalone dvd player. This is the code I am using
[COLOR=Sienna]mencoder <input.mp4> -ovc xvid -oac mp3lame -oac mp3lame -lameopts abr:br=192 -xvidencopts pass=2:bitrate=-700000 -o <output.avi>[/COLOR]
however I get this error:

[COLOR=DarkRed]syntax error near unexpected token `newline'[/COLOR]

[COLOR=Black]Would some kind soul please tell me what's wrong.[/COLOR]

---

### Post by sparker1 on 2011-08-29
Sorry, I worked it out. I had to remove the"<>" characters. Noob

---

