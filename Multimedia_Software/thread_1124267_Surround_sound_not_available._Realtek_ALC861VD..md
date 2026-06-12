---
title: "Surround sound not available. Realtek ALC861VD."
date: 2009-04-13
forum: Multimedia Software
---

### Post by joespra on 2009-04-13
Surround sound options are not available in mixer. Same problem in Hardy, Intrepid and Jaunty. Sound is available from front speakers only.

Shared surround setup - Line in and mic work as surround output.

Tried various suggestions available. Was able to get the surround options (Surround, LFE, Side, etc.,) in mixer by using options snd-hda-intel model=6stack-digout but no sound except from front even with max volume on those controls.

---

### Post by markbuntu on 2009-04-13
Try this

[http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/)

---

### Post by joespra on 2009-04-14
I have tried that without any luck. I think that the problem is that I don't have the 'Line is as output' option in the mixer. I don't even know if model=6stack-digout is the right one for this sound card. It's just that this setting made the surround controls to appear in the mixer.

Anyways, I have just installed OSS and surround seems to be working fine :-) - though only at the osstest level. I'm looking around to find a setup to make the surround speakers to work even when playing stereo.

Thanks for you reply.

Joey.

---

