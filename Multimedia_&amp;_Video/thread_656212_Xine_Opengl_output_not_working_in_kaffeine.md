---
title: "Xine Opengl output not working in kaffeine"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by Metallion on 2008-01-02
Hi everyone

Whenever I use kaffeine (with the xine engine) to play a video file I get really pixelated output. In VLC I was able to solve this by changing the output module to opengl but when I try to use opengl in Xine I get the following message.

```
Error: Can't init new Video Driver opengl - using auto!
```

I'm running Kubuntu 7.10 on an ATI X800 pro. Here's the output of fglrxinfo.

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 PRO
OpenGL version string: 2.0.6473 (8.37.6)

```

Has anyone got an idea what might solve this? I've been looking for extra packages to install or conversation files to thinker with but no luck so far.

---

### Post by Metallion on 2008-01-02
Alright, I've been able to change it the acceptable xv output module by enabling video overlay in my xorg.conf

It would still be nice to figure out how to change it to opengl though.

---

### Post by Nergar on 2008-04-28
bump!

I'm also having the same problem

---

