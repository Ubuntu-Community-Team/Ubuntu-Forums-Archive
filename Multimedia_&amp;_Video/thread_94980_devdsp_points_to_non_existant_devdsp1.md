---
title: "/dev/dsp points to non existant /dev/dsp1"
date: 2005-11-25
forum: Multimedia &amp; Video
---

### Post by art2003 on 2005-11-25
I used to have 2 sound cards but now down to one.

The problem is that at some point I configured things so that /dev/audio and /dev/dsp would link to /dev/audio1 and /dev/dsp1 
Nowadays with just one sound card /dev/dsp1 doesn't exist and nor does /dev/audio1

so I keep having to type
sudo rm /dev/dsp
ln -s /dev/dsp0 /dev/dsp
and the same for /dev/audio

upon reboot it is back to normal

Does anybody know how can I make these changes permanent?
Ideally where is the file I need to edit so the ubuntu creates the links correctly on booting?

---

### Post by scunc_dvl on 2007-03-03
Bump. My TV card is doing something similar, causing /dev/dsp to point to something useless. 

I have alsa configured properly thanks to asoundconf, but /dev/ds* is an oss device thing :/

---

