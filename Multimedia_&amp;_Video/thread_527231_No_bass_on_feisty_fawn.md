---
title: "No bass on feisty fawn"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by Auders on 2007-08-16
Hi, I have a dell dimension 9150 desktop computer running ubuntu feisty fawn. I have a 5.1 surround kit connected to the intel ICH7 sound card (8086:27d8).
The problem is that sound only emerges from the center speaker. There is no bass and no surround.

lspci:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

lspci -n:
00:1b.0 0403: 8086:27d8 (rev 01)

---

### Post by Gremlinzzz on 2007-08-16
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_surround-sound_speakers_.285.1_and_others.29_with_ALSA](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_surround-sound_speakers_.285.1_and_others.29_with_ALSA)
[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

---

### Post by Auders on 2007-08-16
Thanks for the quick reply.
I created a .asoundrc file in my home directory with the text specified in the wiki. The sound still comes only from the front speakers, even after a reboot.
Any hints?

---

