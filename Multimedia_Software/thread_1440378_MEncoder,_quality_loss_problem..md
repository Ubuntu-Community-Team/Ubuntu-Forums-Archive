---
title: "MEncoder, quality loss problem."
date: 2010-03-27
forum: Multimedia Software
---

### Post by Vegar on 2010-03-27
I'm a complete newb when it get's to this. I've managed to convert one file and play it with a free flv player.

Now, the problem is i don't know what parameters that **** up the quality of the file. It get's real bad. :(

```
mencoder in.avi -ofps 25 -o out.flv -forceidx -of lavf -oac mp3lame -lameopts abr:br=64 -srate 22050 -ovc lavc -lavcopts vcodec=flv:keyint=50:vbitrate=300:mbd=2:mv0:trell:v4mv:cbp:last_pred=3 -vf scale=624:352

```
Only thing i've touched is "scale=624:352", so it's the same as the original file.

If what i wrote up there was a little unclear, what i want to do is to:
Covert avi to flv with as little quality loss as possible.

Thanks in advance.

---

