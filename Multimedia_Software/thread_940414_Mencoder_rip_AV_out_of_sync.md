---
title: "Mencoder rip A/V out of sync"
date: 2008-10-07
forum: Multimedia Software
---

### Post by chadjohnson on 2008-10-07
Whenever I rip a DVD (using Hardy) following the multi-pass instructions [here]("http://gentoo-wiki.com/HOWTO_Rip_DVD_mencoder#Multi-pass_encoding"), the audio and video is pretty darn out of sync. Here are the commands I used:
```

mencoder dvd://1 -ovc frameno -o audio.avi -oac mp3lame -lameopts abr:br=128

mencoder dvd://1 -audiofile audio.avi -oac copy -o /dev/null -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=800:vhq:vpass=1:vqmin=1:vqmax=31

mencoder dvd://1 -audiofile audio.avi -oac copy -o dvdvideo.avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=800:vhq:vpass=2:vqmin=1:vqmax=31

```

Any ideas?

Note: I am ripping a DVD I rented from Blockbuster because I have had it for almost a week, and I just want to watch it later and then delete it. Take it as you will, but I'm really being honest.

---

### Post by chadjohnson on 2008-10-07
Ripping using the Xvid codec--as described on that page--works much better:
```

mencoder dvd://# -ovc xvid -xvidencopts pass=1 -alang en -oac copy -o /dev/null
mencoder dvd://# -ovc xvid -xvidencopts pass=2:bitrate=1000 -alang en -oac mp3lame -lameopts vbr=3 -o movie.avi

```

---

