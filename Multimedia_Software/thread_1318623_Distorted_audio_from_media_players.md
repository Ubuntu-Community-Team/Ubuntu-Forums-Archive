---
title: "Distorted audio from media players"
date: 2009-11-07
forum: Multimedia Software
---

### Post by oxf on 2009-11-07
I am getting slightly (not bad but noticeable none the less) distorted audio on playback. This is from playlists and CD's. At first I thought it might be simply the small speakers on this laptop but its present using good quality headphones as well so its obviously the audio stream itself. I'm using Ubuntu 9.04 and this happens with both Rhythmbox and Banshee.
 
OK I know you cant tell me what's wrong based on the brief info above. But how do I start to to track problem down? Is there anything I should check, enter code into terminal to get more info? Or check installed libs etc. Let me know what more info to provide.
 
Many thanks...

---

### Post by oxf on 2009-11-07
I'll add this:

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mbdb@M2000:~$

---

### Post by oxf on 2009-11-08
bump..

---

### Post by Szise on 2009-11-08
Click the Sound/Volume icon, go to Sound Preferences > Applications > choose the one you are using ( example Rhythmbox ) and minimize the volume untill will be no distortion.  Worked for me on 9.10

---

### Post by oxf on 2009-11-08
> **Szise said:**
> Click the Sound/Volume icon, go to Sound Preferences > Applications > choose the one you are using ( example Rhythmbox ) and minimize the volume untill will be no distortion.  Worked for me on 9.10

Thanks,
Hmmm... Well i dont see that option under the sound/volume icon. Of course right clicking does enable to open the volume control sliders and I noticed that PCM was at up at max. reducing it slightly seems to help a bit. I'll play wth it some more. 

But what exactly is PCM? what does it stand for?

---

