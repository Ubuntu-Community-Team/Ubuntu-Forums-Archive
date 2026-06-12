---
title: "Pinnacle PCTV Stereo problems (saa7134 module)"
date: 2005-11-26
forum: Multimedia &amp; Video
---

### Post by pedroleouf on 2005-11-26
Hello all !

I know, there are some threads talking about this, but my problem is in other hand.

I have a Pinnacle PCTV Stereo (Philipps semiconductors) which I try to configure correctly since 1 month...

My problem is that I want to look at the S-Video. But when I run tvtime, the S-Video is on input Television, without sound but image ok, and on the Composite 1, Composite 2 and S-Video input, I have a black screen..... with the S-Video sound !!!!!!

I have configured my module like this:
```
modprobe saa7134 card=26
``` and try diferent tuner=# options without success. I think it's just a problem perhaps with video4linux, which point Television input on S-Video. But I'm on linux (ubuntu) since 2 month only (before I was under the poor Windows system) so I am neerly a newbie.

Someone could help me please, it's a source of stress that having either video or sound..... 

Thx, and sorry for my poor english.

Please help, I lost a rugby match now :-p

---

### Post by pedroleouf on 2005-11-26
Perahps you could help me better with this ?

```

lspci
...
0000:02:0c.0 Multimedia controller: Philips Semiconductors SAA7133 Audio+video broadcast decoder (rev f0)
...

```

It was working on Windows but I hate this OS and no longer want to use it... I've found a lost of answers to my problems in searching google (because I'm a beginner on linux), but I'm locked on this one :-(

Greats thx to the one who could help me

---

