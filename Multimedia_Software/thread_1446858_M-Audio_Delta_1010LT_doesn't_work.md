---
title: "M-Audio Delta 1010LT doesn't work"
date: 2010-04-04
forum: Multimedia Software
---

### Post by joanaomgod on 2010-04-04
I'm using 64bit Ubuntu 9.10 and my sound card is not working. I'v tried to install oss drivers, but there is no effect. Please help!

---

### Post by cchhrriiss121212 on 2010-04-05
This card chip is supported by alsa so you will just need to: disable your onboard sound in bios, then set your output levels. You can do this with a program called envy24control which is in a package called alsa tools in synaptic. Once you've done that I'd avoid using pulse audio as it does not work at all well with my delta.

---

