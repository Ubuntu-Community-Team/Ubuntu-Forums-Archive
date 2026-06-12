---
title: "OSS Kernel Module for 10.10"
date: 2010-10-11
forum: Multimedia Software
---

### Post by commodianus on 2010-10-11
With the eminently providential removal of OSS from the Kernel in 10.10, I'm certain a great many of us could benefit from a guide detailing how to enable it.

The digging I have done as far as building a custom Kernel in Ubuntu has yielded outdated results, and I'm left unsatisfied.

A great deal of games simply do not work without, or work better with OSS.

Is anyone up to writing a guide rather than pointing to some other threads not specific to this issue?

padsp was a sufficient workaround for Quake Wars: Enemy Territory, though the results were not as fruitful with Wolfenstein ET.

Thanks.

(Note: I'm amd64 if that matters).

---

### Post by kotnik on 2010-10-16
Then there's this documentation piece: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

And it seems rather updated to me. Check out if it works for you. I'll have to recompile kernel myself, as well, just for ET, or move to another distro...

---

### Post by Yellow Pasque on 2010-10-16
What? The only thing disabled in the kernel is the old (deprecated) OSS3 modules. If you want OSS, use OSS4. Guides are easily found on the web.

---

### Post by kotnik on 2010-10-17
Just found the solution for ET: [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/)

Follow the first method under 'install', and sound in ET should be working without problems.

---

### Post by commodianus on 2010-10-18
When I install OSS4 I have no sound (for example) at login. Any ideas?

---

### Post by xpatch on 2010-11-04
I just installed 9.04 netbook remix into virtual box so I could use dtmfdial... Only thing I've run into so far that I need oss for...

---

