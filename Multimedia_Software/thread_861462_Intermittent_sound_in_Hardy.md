---
title: "Intermittent sound in Hardy"
date: 2008-07-16
forum: Multimedia Software
---

### Post by barkerben on 2008-07-16
I am running Ubuntu Hardy 8.04
I have onboard sound, but do not use it. Instead I have an Audigy PCI Soundcard 

About 50% of the time, when I boot up there is sound. The other 50%, nothing. I am using the alsa mixer, as OSS seems not to work ever. When there is no sound, if I move the master fader up and down I can hear my speakers crackle, so something is happening...

I have tried:

$ sudo /etc/init.d/alsa-utils restart


Any ideas?

Cheers,

Ben

---

### Post by barkerben on 2008-07-16
Ah - I tyhink it is fixed :-) I checked the BIOS, and the onboard sound was not disabled. 

That does not explain why the sound /sometimes/ worked, but it would seem likely that ubuntu was randmoly picking one or the other to use - and only one had any speakers. That would not seem to explain why wiggling the master fader when the sound was broken made my speakers cracke up and down, but if it works I'm happy :-) I'll need to reboot a few more times to verify it really is fixed...

---

