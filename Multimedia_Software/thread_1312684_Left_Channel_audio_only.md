---
title: "Left Channel audio only"
date: 2009-11-03
forum: Multimedia Software
---

### Post by hwttdz on 2009-11-03
So I was listening to some music and realized I am only hearing the left audio track.  This is likely in part due to having a fancy-pants soundcard and a not fancy-pants speaker setup (i.e. 7.1 or 5.1 I forget which, and 1.0).  Obviously I'd like to be able to hear both tracks.  Currently the only way I can hear the right track is if I open a track in vlc and select audio->audio channels->right, which clearly means I'm not hearing the left track.  

aplay -l
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci doesn't seem to say anything about sound, but I do in fact get sound.  Sound works (i.e. left channel only) if in the sound preferences I set the profile to analog stereo output.

Even if I slide the sound slider all the way to the right side I get no right channel sound (this has the same effect as muting the speaker).

I am using the line in jack to a mp3player dock, so perhaps this is the correct behavior and my question is in fact how to convert stereo input to mono output?

---

### Post by hwttdz on 2009-11-24
Bump.  It would be really nice to get both channels of output, even if I have a single speaker system.

---

### Post by hwttdz on 2009-11-30
Hardware solution:
[http://www.radioshack.com/product/index.jsp?productId=2103725&clickid=prod_cs](http://www.radioshack.com/product/index.jsp?productId=2103725&clickid=prod_cs)

In my opinion I think this is a better solution, however I think the ability to direct both channels to either the left or the right channel should exist/be more accessible.

---

