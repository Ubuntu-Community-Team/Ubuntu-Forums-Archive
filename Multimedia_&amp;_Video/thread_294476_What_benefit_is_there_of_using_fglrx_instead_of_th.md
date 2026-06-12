---
title: "What benefit is there of using fglrx instead of the open-source drivers?"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by Extreme Coder on 2006-11-06
Hi there.
I wanted to know if there's any benefit for me to change from the open-source  ati and radeon drivers to the fglrx ones distributed by ATI, provided I have a Radeon 9200 SE. Will it gain more speeds or so?

Thanks.

---

### Post by Joe_CoT on 2006-11-06
In general, you will see a speed increase with the binary fglrx drivers.

The only downside to using the binaries is that fglrx does not yet support composite extensions, which are necessary to use AIGLX/Beryl. Using the fglrx driver, you need to use XGL to use Beryl.

---

### Post by Extreme Coder on 2006-11-06
Pardon me, but whats:
Beryl?
AIGLX?
XGL?
I've heard of those names before, and I guess this would be a good chance to figure them out:)
Thanks.

---

### Post by Joe_CoT on 2006-11-06
:cool:
XGL is a reference implementation for adding 3d effects to x-window, as originally coded by programmers at novell. For the most part, it's a hack -- it runs on top of X-window, is very buggy, uses a lot of processor power, and steals all of X window's opengl rendering. However, it is very impressive, and I used it from CVS the moment I saw the video.

Compiz was the reference window manager which came out with xgl. It includes a lot of neat effects (window animations, transparency, cube desktop, etc).

AIGLX is an extension to X Server. It does everything that XGL does, but it's not a hack, and it's actively developed. Everyone not using the binary ATI driver uses AIGLX. AIGLX comes enabled by default in Edgy Eft

Beryl is a child project of Compiz, and for the most part its successor. It's fairly stable, adds more effects, and (apparently) is going to be included in Feisty Fawn.

---

### Post by mlw4428@gmail.com on 2006-11-06
> **Joe_CoT said:**
> :cool:
XGL is a reference implementation for adding 3d effects to x-window, as originally coded by programmers at novell. For the most part, it's a hack -- it runs on top of X-window, is very buggy, uses a lot of processor power, and steals all of X window's opengl rendering. However, it is very impressive, and I used it from CVS the moment I saw the video.

Compiz was the reference window manager which came out with xgl. It includes a lot of neat effects (window animations, transparency, cube desktop, etc).

AIGLX is an extension to X Server. It does everything that XGL does, but it's not a hack, and it's actively developed. Everyone not using the binary ATI driver uses AIGLX. AIGLX comes enabled by default in Edgy Eft

Beryl is a child project of Compiz, and for the most part its successor. It's fairly stable, adds more effects, and (apparently) is going to be included in Feisty Fawn.

If that isn't clear enough basically XGL is a piece of software that allows  you to do neat 3D effects (as well as other things). Compiz is a Window Manager and it defines ways of doing those 3D effects (for example you can have your windows "wobble" when you move them). Beryl used to be part of Compiz, but due to some issues a group decided to split and begin working on adding features that the other developers of Compiz didn't want to do. :cool:

---

### Post by johnaaronrose on 2007-04-23
I've tried installing Beryl with XGL as per a blog giving instructions for Dell Inspiron 1501 laptop using Feisty which also stated that the ATI8.34.8 driver should be installed using the Restricted Driver Manager (which I did) and that beryl-core should be downgraded to a version supplied by lupine.me.uk. It doesn't work (i.e. no cube, no fading windows etc) with last week's release of Feisty when beryl & beryl-manager are started for an xgl session. 

So I thought I'd try using AIGLX, as it is recommended (on various threads) over XGL. From various threads, it looks like the open source driver is needed for the ATI XPRESS card: is that correct? If so, where may I obtain the open source driver for the card? 

The packages I previously installed were xserver-xgl, beryl-ubuntu, beryl-manager, emerald-themes. Are there any others needed for AIGLX & Beryl?

---

