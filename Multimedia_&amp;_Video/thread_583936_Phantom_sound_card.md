---
title: "Phantom sound card?"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by Lacclolith on 2007-10-20
I've tried just about every fix that I've found through searching Google/forums/Linux howto's. None have worked. I'm at the end of my rope, and am just about at the point of reinstalling from scratch.

I'm running Ubuntu 7.04 on a machine with a VIA82xx sound device on it. At one point in time, a Soundblaster Audigy was connected to this machine, but was removed. Now, many programs have no sound output. I've already confirmed that the card is no longer present in the alsa mixer, and I've even gone so far as to force my sound device to VIA82xx manually though the terminal. Sound is fine in firefox and media player applications, but the shell sounds (such as the startup noise) don't play in anything except the aforementioned media players, and ZSNES (1.51) doesn't output sound at all. When trying to run ZSNES, I receive errors such as:

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'Audigy'

and

ALSA snd_pcm_open error: No such device

I get this error when trying to run other programs. for instance, when trying to  sudo gedit /etc/modules, I still get a "ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'Audigy' " error. It would seem as if the system still thinks the card is connected, but I can't find any traces of it. One person vaguely suggested that I uninstall the driver for the Audigy card, but I can't figure out how to do that, even. What can I do to fix this?

---

