---
title: "ATI and Composite effects"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by hartz on 2007-06-05
I am busy setting up an extra computer with Xubuntu and now trying to get the xfce Composite effects to work on an ATI card ... but it is slow and jerky whenever I enable any special effects like transparency on Move.

Now after having read many howtos, driver install guides, and answers to other people's problems, I have a question:  Are there two different things called "fglrx"?

Some posts implies that there are.  People have made comments along the lines of "If you have had the ATI driver installed from the Restricted Drivers package previously, then add fglrx to the DISABLED_MODULES line in the file /etc/default/linux-restricted-modules-common"

However it would seem that the ati proprietary driver is also called fglrx ?  

A few more questions:  What combination should I use:
xorg or xgl
ati or radeon or fglrx
Ubuntu restricted driver or ATI proprietary driver, and which version?  8.37.6 ?
xfce or enlightenment

P.S I have a Radeon 9550 and Xubuntu 7.04.  I am about to throw the ATI card in the bin and go back to my ancient MX440 card.

Thanx!

---

### Post by dodgePT on 2007-06-05
I own an ATI 9600 pro and i'm using radeon (open source drivers)+AIGLX. Beryl works great with this setup, but there's a glitch, with movie playback.

First I tried fglrx+XGL, but had nothing but trouble. Try both setups, and choose the one that gives you better results ;)

---

### Post by hartz on 2007-06-05
Since posting my question I've found several explanations stating that Compositing does not work with XGL, yet Beryl+fglrx+XGL does work?  Is the compositing aspect of Beryl not the same as the compositing found in Xfce?

I must say I find this all very confusing.

In some posts I've seen Compositing is expressly disabled in the xorg.conf file, and in others that AIGLX is disabed, but there is never an explanation of why.

In [this post]("http://ubuntuforums.org/showthread.php?p=2778036#post2778036") PandaGoat seems to be half-confirming this...

---

### Post by dodgePT on 2007-06-05
In Wikipedia, [AIGLX]("http://en.wikipedia.org/wiki/AIGLX") and [XGL]("http://en.wikipedia.org/wiki/Xgl"):

> Rationale

There are two ways that a windowing system can allow an OpenGL implementation to talk to the graphics card.

The first is to specify the OpenGL command stream in a portable network-neutral manner using a client/server implementation similar to the X11 drawing routines. This is the indirect route as the drawing commands are sent to the X server and then the X server sends them along to the graphics card.

The second way, which is at the base of Xgl, is to open a window and then allow the OpenGL library to send commands directly to the graphics card. Accelerating the indirect OpenGL path is orthogonal to how the X server itself is implemented, but it has the side effect of allowing the OpenGL command stream to be more easily captured and redirected to a texture. This allows Compiz and other compositing window managers to be built on top of a traditional server with a small GLX extension rather than requiring a full Xgl server. Another advantage is that DRI bypasses the Xgl server (so it can not be accelerated), while with AIGLX everything is allowed to be composed.

---

