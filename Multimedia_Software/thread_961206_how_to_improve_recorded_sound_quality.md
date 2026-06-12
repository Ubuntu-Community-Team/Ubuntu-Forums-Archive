---
title: "how to improve recorded sound quality"
date: 2008-10-28
forum: Multimedia Software
---

### Post by sensius on 2008-10-28
hi folks,

I'm trying to record a short sound with Ubuntu recorder (using Sound Recoreder). After some attempts (searching this forum, try all options), now I can record some sound. But the quality is not as expected (it seem that there's lots of noise). Does anyone know how to improve this?

many thanks

---

### Post by Amazona aestiva on 2008-10-28
> **sensius said:**
> hi folks,

I'm trying to record a short sound with Ubuntu recorder (using Sound Recoreder). After some attempts (searching this forum, try all options), now I can record some sound. But the quality is not as expected (it seem that there's lots of noise). Does anyone know how to improve this?

many thanks

Hi!

Well, if you want to remove noise from a sound track use Audacity and if I were you I would use Audacity to record the sound too.
It's in the repo, just type:
```
sudo apt-get install audacity
```

Regards

---

### Post by sensius on 2008-10-28
Thanks Amazona aestiva for your quick reply. I'll try your suggestion.

Now I want to see the problem under the developer's point of view. Does this mean that if I want to develop an audio recording program then I have to take care of noise filtering/reduction myself?

---

### Post by Amazona aestiva on 2008-10-28
> **sensius said:**
> Thanks Amazona aestiva for your quick reply. I'll try your suggestion.

Now I want to see the problem under the developer's point of view. Does this mean that if I want to develop an audio recording program then I have to take care of noise filtering/reduction myself?

Noise is not default and it shouldn't be on the recording. It may come from the too loud volume levels, old source(VHS tapes for example), bad cables or jacks.

The noise reduction can't be used at realtime recording(at least not so high quality I suppose). "Do you have to take care of noise reduction?" Not really. There are softwares which can do that, and even those don't filter the sound at recording time. However if you want your program to have such filter, look for a plug-in, ask some experianced develpper how to implant it, and visit mailing lists.

Just my opinion.:)

Regards

---

### Post by markbuntu on 2008-10-28
Make sure that all the capture sliders in the volume control or sound mixer are muted except the one you are using. For example, if you are recording from line in and you have the mic capture on, it can generate noise even without a microphone attached. Also, if you are recording from a mic use the mic boost option if it is available. This will raise the mic level above the noise.

Some application developers make assumptions about hardware. Only the sound server really knows what is going on with the hardware so these assumptions fail eventually. Noise like you describe is not a concern with application developers, it comes from the sound server and the low level drivers, usually because of faulty assumptions made by users or the driver writers. The newer nvidia hda embedded mobo sound chips have a problem with noise and crackling due to poorly configured firmware and naive assumptions by the driver writers. This has been fixed in the 2.6.27 kernel which is available in Intrepid.

---

### Post by sensius on 2008-10-29
Thanks all guys for clarify it. I tried to mute some volume controls and it did reduce some noise :) (but actually I still want something better :guitar:

---

### Post by Vubu on 2008-12-07
Hi!
I have the same problem. 
But I think the problem is not in hardware, because Windows records sound at same mic and soundcard much more better. It seems that problem is in sampling rate... 

I tryed to start system with option 

      append="no-hlt"

 but it brings small result.

Does anybody has an idea how to solve this?

---

