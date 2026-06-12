---
title: "Flash problem"
date: 2009-11-16
forum: Multimedia Software
---

### Post by m0rbidpercepti0ns on 2009-11-16
Im currently runnin 8.10 because it seems to be more stable for my PC than 9.04 or 9.10. My problem is that i dont have sound in flash,in firefox 3.0. I have done a fresh install of adobeflash-plugin-nonfree,and the nonfree-extrasound.Ive installed ALSA-OSS and changed the wrapper in FirefoxRC to use OSS,and that didnt help. Ive been goggling and searching my heart out,and i cant seem to find a fix.So far ive spent close to 20hrs trying to figure this out..and i cant seem to get it. I dont have AWF or Gnash installed.Pulseaudio shows a moving volume meter when i play a video on Youtube..so i know its working, i just dont understand why i cant hear it. any help is GREATLY appreciated. Thanks in advance.

Ok- so IMMEDIETLY after posting for help, i found the solution.The problem was that i have 2 soundcards,and i was watching the volume meter in pulse move,Then i opened volume control,and looked at playback.the little arrow next to the mute and use button>clicked it,and pushed move stream,and i moved it onto the other soundcard i have. Apparently pulse automatically tried to use my internal card,even though everything is set to my Audigy card...that was the solution,should anyone else have this simple issue.

---

