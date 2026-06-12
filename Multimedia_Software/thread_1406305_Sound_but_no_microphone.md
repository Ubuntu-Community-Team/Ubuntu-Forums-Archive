---
title: "Sound but no microphone"
date: 2010-02-13
forum: Multimedia Software
---

### Post by naiku on 2010-02-13
I have a Dell Latitude D830, and installed Skype earlier today. But, I have a weird problem with the sound. If I get the sound to "Digital Stereo (IEC958) Output + Analog Stereo Input" then I have no sound, but the microphone works. If i select "Analog Stereo Ouput" I have sound, but no microphone. 

If I use external speakers, then I can have sound + microphone using the IEC958 option, but I don't want to have to haul around external speakers with my laptop. 

Do I need to look for an updated driver? or is there some way to get the Analog Stereo Output + Analog Stereo Input working together? 

Thanks.

---

### Post by RedSingularity on 2010-02-13
Do you have pulseaudio installed?

---

### Post by naiku on 2010-02-15
> **RedSingularity said:**
> Do you have pulseaudio installed?

No, should I install it?

---

### Post by RedSingularity on 2010-02-15
Ahhh actually not yet.  In a terminal type "alsamixer" and make sure all the capture volumes are up all the way.

---

### Post by naiku on 2010-02-17
It looks like that did the trick, the weird thing is I increased the capture volume levels whilst my laptop was in the docking station. After I removed it and went back into alsamixer the capture tabs were no longer there, and no longer show up while in the docking station. I do now have microphone and sound when docked and undocked. I just have to remember to switch between digital and analog.

Thanks.

---

