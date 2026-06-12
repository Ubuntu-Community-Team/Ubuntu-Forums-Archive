---
title: "Problems with ubuntu sound"
date: 2008-08-23
forum: Multimedia Software
---

### Post by toxirau on 2008-08-23
Hey im newish to ubuntu and im planing on switching my desktop over to ubuntu. I installed it updated and all and then when i tried to enable 5.1 for my headphones i couldent get it to work or notice that i had a 5.1 sound card. So i started searching on the net for a tutorial or something, and I found a few and none of them seamed to work.( [http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/](http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/) ) I have a ECA A780GM-A with IDT 92HD206 sound, the card supports 8 channel suround and uses the SigmaTel ID 7645 codec. Im not sure what to do from this point. 

Here is a screen shot of my sound config and controler
[http://img245.imageshack.us/img245/9350/soundproblemsbt8.png](http://img245.imageshack.us/img245/9350/soundproblemsbt8.png)

---

### Post by nilnet on 2009-04-14
I have a similar issue with this board and chipset, though I use Ubuntu Studio 8.04.1 amd64. I have audio playback only. No resources for audio capture or recording are found, so its not much good for studio which I intended. I temporarily installed and older supported card and disabled the mb audio.  
I think has to do with the behavior of the audio port detection and logic used to determine whether input or output , like mic or headphone or speaker...In windoz the ECS provided driver will detect the plugging of a headphone or mic appropriately.

---

