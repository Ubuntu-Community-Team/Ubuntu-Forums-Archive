---
title: "problem with playing wmv in mplayer."
date: 2008-07-20
forum: Multimedia Software
---

### Post by a.dehqan on 2008-07-20
In The Name Of GOD
Hello

I will be thankful if you guide me .
When ever i want to play .wmv files with Mplayer it gives [This error]("http://i38.tinypic.com/29mnlut.png") .
How can i solve it ?
Which codec package should i copy from [this address]("http://www1.mplayerhq.hu/MPlayer/releases/codecs/") that will be enough?

I use debian etch 4 ,kernel & cpu 32bit 
regards dehqan

---

### Post by shirilover on 2008-07-20
You don't need to install a codec package to fix that problem.
You should specify the video output like the following examples:

-vo xv
or -vo gl
or -vo gl2

Another method is to add a line in your ~/.mplayer/config file

#Use the following video ouput, in order of preference
vo=xv,gl2,gl

---

### Post by a.dehqan on 2008-07-20
In The name Of GOD
Hello

Thanks alot for you'r attention .
I changed video driver and it's ok NOW and i can play .wmv files now with no problem .
But when i want to play [this url]("mms://media1.iransima.ir/AmouzeshTV/AmTV_13870424_007.wmv") with mplayer it gives me [this error]("http://i38.tinypic.com/11rexs8.jpg") ?
Is it because of that ,server is busy ?

Thanks alot
regards dehqan

---

### Post by shirilover on 2008-07-20
OK, now we specify the audio output.
Personally, I prefer using SDL (-ao sdl).
You can also try -ao pulse or -ao oss.

---

### Post by a.dehqan on 2008-07-20
In The Name Of GOD
Hello

I'm so Thankful for you'r guides and attentions.
I specified audio out put know when i test [that link]("mms://media1.iransima.ir/AmouzeshTV/AmTV_13870424_007.wmv") with open url gives [this error]("http://i37.tinypic.com/256fmh2.jpg") ,I will be thakful if you guide me .
Does that link work for you ?can you see movie ?

regards dehqan

---

### Post by xc3RnbFO8P on 2008-07-20
Its a server problem, I get sound 10 sec then it stops
and I get 1 frame video, then it start buffering again.

---

### Post by a.dehqan on 2008-07-21
> **Ringi said:**
> Its a server problem, I get sound 10 sec then it stops
and I get 1 frame video, then it start buffering again.

In The Name Of God
Hello

I'm so Thankful for you'r attentions and guides .
Would you tell me what you'r internet speed is ?

Thanks alot

---

### Post by a.dehqan on 2008-07-24
In The Name Of God
Hello

Can we play .dat files in mplayer ?

Thanks

---

### Post by shirilover on 2008-07-24
.dat files are mpeg-1 program streams with RIFF headers, commonly known as a VCD.

you could try --
mplayer vcd://1

---

