---
title: "help with jackaudio, pleeeease?"
date: 2012-02-25
forum: Multimedia Software
---

### Post by ohnonot on 2012-02-25
so i installed the whole ubuntu studio pack and notice most of the apps use/want/depend on jackaudio...
some jack software had been installed too, and i installed some more.

(sorry for being unprecise here, i just don't remember anymore but will provide a list if someone would look into my problem)

(also i realise there's loads of articles about exactly this, i checked out about 3 of them and followed the steps, but still...)

after realising that jack is working i uninstalled pulseaudio.
now i'm having a very hard time trying to set all this up properly.
basically, running one audio app works, but when i try to run another one (at the same time or after closing the first) it usually returns an error message "no audio device found or busy" - something like that.
also some apps don't seem to support jack, like my beloved shell-fm :-(
but i heard there's workarounds but again, how...

alsa is still working but seems to have suffered???

all help appreciated.
):P

i'm running xubuntu 11.10 and have replaced the kernel with the newest (3.2.x) with rt-patch. no problems there.

my hardware is old, so i'm trying to save or make best possible use of my resources.

---

### Post by ohnonot on 2012-03-01
solved?
not sure what i did, but after a while jack started working properly.
qjackctl is definitely helpful, almost mandatory if you're no command line god.
there's articles in ubuntu help about how to set it up.

about shell-fm: there's a workaround: use an external player (e.g mplayer) for output. see man shell-fm.

mocp still doesn't work properly, though it does support jack - i have to connect it manually every time. mayb i get that solved, too.

---

