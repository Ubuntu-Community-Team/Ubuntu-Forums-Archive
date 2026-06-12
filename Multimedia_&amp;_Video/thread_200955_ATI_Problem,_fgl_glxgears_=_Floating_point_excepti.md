---
title: "ATI Problem, fgl_glxgears = Floating point exception?"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by Knight on 2006-06-21
Just got a new laptop with 1 gig of ram, 1.8ghz 64bit AMB, and a ATI Radeon Xpress 200M Video card. Have been trying to get World of Warcraft working with wine to a playable degree with limited sucess. Theres the "not being able to click stuff" problem that seems common with us WoW'ing ATI'ers, but while manageable, the FPS blows. While trying to hunt down the problem, I noticed when I try to run fgl_glxgears I get this:
```
Using GLX_SGIX_pbuffer
Floating point exception
```
And then nothing happens. I've installed the laptop ATI drivers from the ATI site. fglrxinfo returns:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5814 (8.25.18)

```
Does anyone know how to fix this? Or if I'm even on the right track to fixing the WoW lag issue? Also, sorry if this is the wrong section to post. I wasn't sure if this should go in Gaming, AMD64, Laptops, or here. So many subforums... arg. Any insight is welcomed, thanks in advance.

---

### Post by JamesLast on 2006-06-29
[http://ubuntuforums.org/showthread.php?t=162134&highlight=fgl_glxgears+floating+point+exception](http://ubuntuforums.org/showthread.php?t=162134&highlight=fgl_glxgears+floating+point+exception)

[http://ubuntuforums.org/showthread.php?t=189848&highlight=fgl_glxgears+floating+point+exception](http://ubuntuforums.org/showthread.php?t=189848&highlight=fgl_glxgears+floating+point+exception)

Using the search-options before posting sometimes shows results :)

Problem exists at least on 9600, x700 and you card, Problem exists since 8.23, no soultion know.

cheers James

---

### Post by JamesLast on 2006-06-30
There is an bugzilla entry on the unofficial ati bugzilla:

See here
[http://ati.cchtml.com/show_bug.cgi?id=453](http://ati.cchtml.com/show_bug.cgi?id=453)

cheers

---

### Post by jkwarras on 2006-07-05
I'm having the same problem. I have a Radeon X700. When I run glxgears it runs without problems, only fgl_glxgears returns the floating point exception. So, at then end I really don't know if i have a problem or not...

---

