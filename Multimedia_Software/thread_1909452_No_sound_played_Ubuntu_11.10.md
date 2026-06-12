---
title: "No sound played Ubuntu 11.10"
date: 2012-01-15
forum: Multimedia Software
---

### Post by ubunkid on 2012-01-15
I have a Dell 1564 and I recently freshly installed Ubuntu 11.10. No sounds are played either with headphones or speakers, not even the start-up Ubuntu sound. Any way to solve the issue?

---

### Post by ubunkid on 2012-01-20
No suggestions at all? :(

---

### Post by iliis on 2012-01-20
Well, a lot of things could cause that. Obvious stuff first: Is the volume up on _everything_? Often laptops have special keys for volume and this is sometimes independent of Ubuntu (look for some function-key (Fn) or something). Also try to turn up everything (and down, just for fun) and play with the controls.

If this doesn't help, try some of the various sound troubleshooting guides:
[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1)
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Also, try to post more information about your system.
Eg., execute this:

```
**wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) && bash ./alsa-info.sh --upload;**
```
Cheers, iliis

---

