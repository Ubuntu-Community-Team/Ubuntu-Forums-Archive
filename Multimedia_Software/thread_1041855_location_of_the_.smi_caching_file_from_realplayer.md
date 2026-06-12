---
title: "location of the .smi caching file from realplayer"
date: 2009-01-17
forum: Multimedia Software
---

### Post by afeasfaerw23231233 on 2009-01-17
When I use realplayer to listen radio programme archive, it starts caching up the whole audio file. Can I copy that file to a mp3 player? Where is that temporary file locate? Thanks! 

Here's the link: [http://www.rthk.org.hk/smi/rthk/radio3/pierre/20081121.smi](http://www.rthk.org.hk/smi/rthk/radio3/pierre/20081121.smi)
It's a old radio programme and not a live radio stream.

---

### Post by andrew.46 on 2009-01-18
Hi,

I am not familiar with RealPlayer but what you want can be done with MPlayer and lame:

```

$ cd Desktop
$ mplayer -cache 1024 -playlist http://www.rthk.org.hk/smi/rthk/radio3/pierre/20081121.smi -vc null -vo null -ao pcm:fast:waveheader:file=radio.wav
$ lame -b 128 --resample 44.1 radio.wav radio_show.mp3

```

lame options could do with a little fine-tuning, I am more used to Ogg Vorbis :-).

Andrew

---

### Post by afeasfaerw23231233 on 2009-01-20
thanks

---

