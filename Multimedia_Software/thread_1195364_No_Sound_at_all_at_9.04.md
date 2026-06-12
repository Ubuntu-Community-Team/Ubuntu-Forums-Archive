---
title: "No Sound at all at 9.04"
date: 2009-06-23
forum: Multimedia Software
---

### Post by cnand on 2009-06-23
I dont have any sound at 9.04 and i dont know what to do.
i just tried 
 
aplay -l

and i get that

card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am trying and i am changing all the options at the sound options and the only sound i get while playing music is from the pc speaker on the case...
How do i change that to get the sound in the jacks?
Thank you in advance i would appreciate any kind of help cause it is really sad not to have any sound at all...

---

### Post by ratcheer on 2009-06-23
I had a similar problem. I solved it by adding my username and root to the three pa* user groups. They should be there to start with, but it is a known bug in 9.04. Hope this helps.

Tim

---

