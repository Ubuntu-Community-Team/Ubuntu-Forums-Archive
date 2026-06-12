---
title: "Video Playback Woes :-("
date: 2010-09-07
forum: Multimedia Software
---

### Post by Zahne on 2010-09-07
Hey all,

I've got a set up with an Nvidia Geforce 8400 card and I'm notcing a lot of choppiness in the playback. I did a search and found this guide.

[http://ubuntuforums.org/showthread.php?t=239617]("http://ubuntuforums.org/showthread.php?t=239617")

It's from '06 so I wonder if that's why I'm not yielding the same results. 

In step 1, I was able to verify OpenGL and got this result:

```

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 8400 GS/PCI/SSE2
OpenGL version string: 3.2.0 NVIDIA 195.36.24
OpenGL shading language version string: 1.50 NVIDIA via Cg compiler
OpenGL extensions:

```

Step 2 asks me to make sure that the opengl libraries are linked properly. That works when I receive this result:

```

lrwxrwxrwx 1 root root 19 2010-09-07 10:07 /usr/lib/libGL.so -> /usr/lib/libGL.so.1

```

Then when it comes time to enable vsync, I'm asked to put in this code:

```

export __GL_SYNC_TO_VBLANK="1"

```

Above this:

```

if [ -r /etc/environment ]; then
  if LANG=$(pam_getenv -l LANG); then
    export LANG
  fi
  if LANGUAGE=$(pam_getenv -l LANGUAGE); then
    export LANGUAGE
  fi

fi

```

The problem is that I can't seem to find the "if [ -r /etc/environment..." lines anywhere in the file that 'm supposed to edit. Should I just add that in it too? Is there a different way to enable vsync for 10.04 and my card? 

Any input would be much appreciated.

---

### Post by cchhrriiss121212 on 2010-09-07
That guide is about compiz and DVD playback issues, and is probably a bit outdated. Are you having trouble just with DVDs or all video playback ie .avi or .mkv files?
What player are you using?
You could see a noticeable difference if you upgrade to the latest drivers, which is 256, but that may not be necessary.

---

### Post by Zahne on 2010-09-07
Thanks for the response. Yes it's with general video playback. I did not find the 256 drivers in synaptic. Is it something I need to get through terminal?

---

### Post by jamessimo on 2010-09-07
I had the same problem! Its a simple fix! (I use Nvidia GeForce 260Gtx and was weired out by the cutting) 

Get ccsm (Compiz manager)

Open ccsm in System > Preferences > ComplizConfig Settings Manager

Inside of ccsm goto General > General Options > Display Settings > Sync to VBlank.

This should hopefully fix it! 

(I made all the nVidia drivers and settings VSync, but I think at the end of the day, compiz is were the frames bottle neck. Its not your card or drivers in my opinion.)

---

### Post by Zahne on 2010-09-07
It worked! Thanks so much for the help!

---

### Post by Linuxforall on 2010-09-07
I have the same card here, video is absolutely glitch free, no choppiness on HD movies full screen, I compile my own mplayer with vdpau using Andrew's instructions from the tutorial section. If you don't feel like compiling, add RVM's ppa for mplayer and smplayer and in smplayer video preferences, select vdpau and you won't have any issues. I would also suggest you add x-swat ppa for latest nvidia driver.

---

### Post by jamessimo on 2010-09-08
> **Zahne said:**
> It worked! Thanks so much for the help!

Your more than welcome! Glad to help!

---

