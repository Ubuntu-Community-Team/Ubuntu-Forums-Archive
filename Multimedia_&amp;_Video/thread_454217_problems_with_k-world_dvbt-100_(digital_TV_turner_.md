---
title: "problems with k-world dvbt-100 (digital TV turner card)"
date: 2007-05-25
forum: Multimedia &amp; Video
---

### Post by lockpicker on 2007-05-25
Hi, i've the k-world dvbt-100 tv card but i don't know how install it on feisty fawn.
I've read that the chipset cx23880 is supported by current kernel so it have to work.
In Kaffeine there isn't the tv button so i've tried with xawtv too but when v4linux-conf start my monitor come black.

This is the v4linux-conf output:
```

v4l-conf: using X11 display :0
dga: version 2.0
mode: 1280x1024, depth=24, bpp=32, bpl=5120, base=0xe0000000
/dev/video0 [v4l2]: no overlay support

```

I think that isnt a front end problem (i've tried with kdetv mplayer and others) but a card's problem.

This is the lspci output:
```

02:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:05.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

```

I've never configurated a tv turner so i've no idea how fix it.
I hope that someone can help me.

Thank's

Andrea

---

### Post by steefjeqv on 2007-05-26
Hi,

Have you tried :

sudo modprobe cx88-dvb

Greetings,
Steven

---

### Post by lockpicker on 2007-05-27
Thx so much :)

I've thought that the module was loaded by default :lolflag:

---

### Post by steefjeqv on 2007-05-27
Hi,

After detecting your DVB device, Feisty should load the module. But it doesn't.

To make Feisty load this module upon boot add cx88-dvb to your modules file.

sudo gedit /etc/modules

And just add cx88-dvb.

Greetings,
Steven

---

