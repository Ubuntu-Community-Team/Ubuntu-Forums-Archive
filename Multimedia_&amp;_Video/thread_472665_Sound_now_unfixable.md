---
title: "Sound now unfixable"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by utopial on 2007-06-13
Hey,

I've got a pretty old sound card (creative SB Live! - emu10k1) and originally when i installed ubuntu feisty fawn a few weeks ago my sound worked.
i noticed that whenever i installed programs and restarted that my sound stopped. i found the solution to get the alsa drivers from a fresh kernel from this site: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
it worked fine. everytime i installed something and the sound stopped, i'd do that and my sound would start working again

then tonight i accidentally installed daemontools-installer and its dependencies from synaptic package manager. when i restarted the sound was gone. i uninstalled daemontools and its dependencies and then did the alsa driver fresh install several times but my sound never works anymore. i didnt get any error messages when i did the alsa driver fresh install either

also, i should note that when i first noticed my sound stopped working and uninstalled daemontools, i was also in the middle of trying to install cdemu which is currently causing a lot of feisty fawn users problems and when i did install it i got some error like '/bin/sh: Syntax error: Bad fd number cdemu' altho the install ended up going thru fine.

im pretty lost, but perhaps someone can make something of this. is there any reason y the fresh sound install no longer works?

---

### Post by utopial on 2007-06-13
when i turned on my comp this morning the sound worked.
when i get home from work ill turn it on again and see if it works. i suspect that it wont
what usually happens when i install programs is that the sound only works on about 20% of the restarts if i dont do the fresh kernel alsa install. after i do the fresh kernel thing, sound works on 100% of the restarts, which currently isnt the case.

---

### Post by utopial on 2007-06-14
ok sound is screwed again
so it's working about 20% of the times that i start my comp
nfi wat is going on

any ideas?

---

