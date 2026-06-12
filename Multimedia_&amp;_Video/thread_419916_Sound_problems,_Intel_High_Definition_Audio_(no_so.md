---
title: "Sound problems, Intel High Definition Audio (no sound)"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by sindrejh on 2007-04-23
Hi,
I have been working around trying to get my sound to work, a lot of hours now. But now I have nearly given up, so some help would be nice.

It's an Acer Ferrari 1000 laptop, witch I earlier (in Edgy) have got sound on with t[his driver]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2").

But now I can't manage to install that, when I comes to the "alsaconf" point it just gives me:
```

modinfo: could not find module snd
modinfo: could not find module snd
modinfo: could not find module snd
modinfo: could not find module snd-opl3sa2
modinfo: could not find module snd-cs4236
modinfo: could not find module snd-cs4232
modinfo: could not find module snd-cs4231
modinfo: could not find module snd-es18xx
modinfo: could not find module snd-es1688
modinfo: could not find module snd-sb16
modinfo: could not find module snd-sb8
```

lsmod | grep snd gives nothing and lspci says:
```

00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
```

Is someone having any good ideas?

---

