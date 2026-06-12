---
title: "No sound from flash applets, Kubuntu 9.04"
date: 2009-09-12
forum: Multimedia Software
---

### Post by annihilan on 2009-09-12
I use a USB headset in place of speakers, and I cannot get sound to emit from either Konqueror, Opera, or Firefox from things like youtube.com or playlist.com.

I'm not really fluent in Linux, so don't assume I am. :)

I followed Opera's instructions for installing mplayer, but encountered an error when I did ./configure, something along the lines of C++ can't build packages, or execute packages. It was odd. I tried installing gxine, which installed, but didn't seem to support sound. I can *see* the video, but they don't make sound.

I'd really like help :/

cat /proc/version returns:
```

Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009

```

---

### Post by sudo panda on 2009-09-12
you could check if you've got g++ installed
that could cover your C++ error when building..
as for the sound in flash you might want to check that you've got the flashplugin-nonfree-extrasound package installed.
both should be in your package manager (i think its kpackagekit in kubuntu?)

---

### Post by annihilan on 2009-09-13
G++ is installed, and libflashsupport.so, even when put into Opera's plugin directory, isn't found. Does it automatically supplement one of the other plugins, or are you supposed to configure your browser to use it?

I also can't seem to get Konqueror to use a certain plugin, it saw something, but it's not a selectable list, just there for information.

---

