---
title: "Problems recording output from speakers."
date: 2007-09-16
forum: Multimedia &amp; Video
---

### Post by frederick1978 on 2007-09-16
Dear all,
I'm currently running on Ubuntu Feisty 7.04 and with audio HDA NVidia.

With Audacity everything seems working fine if I try to record from the Microphone, selecting the option < Front Mic > in the Options tab of Alsamixer.
However if I select < Line > and I try to record the sound played by the PCM, nothing gets recorded.

I don't think that this is a problem with Audacity, in fact I cannot record the PCM audio even using other software such as RecordMyDesktop.

I tried to follow even the instruction suggested in the wiki of Alsamixer, but when I type the commands
amixer set 'Mix' cap
or 
amixer set 'Capture' cap
I always get  
Unable to find simple control ...:(

Any ideas?

Thanks a lot for your attention.

          Regards

                    Federico

---

### Post by lisati on 2007-09-16
I'm not sure of the solution, but sometimes recording problems can sometimes depend on the kind of sound card you have in your machine. The term "duplex" comes to mind, again I'm not sure of the relevance.

---

### Post by frederick1978 on 2007-09-17
Thanks for your reply,

it seems that I am not the only one having the same sort of problem.

I posted my question here with the hope that someone already encountered and solved the problem.

Thanks anyway.

Regards
       Federico

---

### Post by Steinle on 2008-02-07
i got the same problem...

i can record with the build-in microphone, i can record with external microphone, but i never get to record the "internal" output :/

---

