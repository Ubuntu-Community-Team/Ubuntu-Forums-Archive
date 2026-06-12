---
title: "No audio input on 11.04"
date: 2011-05-28
forum: Multimedia Software
---

### Post by ChrisKu on 2011-05-28
After having solved my audio output problem thanks to the help of this great community I am struggeling again - this time with audio input. I am trying to record using a microphone without success. Checking my audio settings on the input tab all remains silent. I also checked the input channels using alsamixer and all looks correct.

My Alsa information can be found here:
 [http://www.alsa-project.org/db/?f=c22e598b48b81d4fc59ed24725dbffc255c31ea5](http://www.alsa-project.org/db/?f=c22e598b48b81d4fc59ed24725dbffc255c31ea5)

Would be really grateful for any hints.

Chris

---

### Post by ChrisKu on 2011-05-29
Looks like I solved the problem. Must have been due to settings in Alsamixer. I started Ubuntu from a Live CD - the microphone worked in that environment. I then started Alsmaixer and made a note of all the seetings there. 
Then I rebooted into my normal environment, started Alsamixer and set all channels to the values I noted in the LiveCD environment. And voila - all worked nicely. 
The main differences where in the Capture area where I had set all channels to max values. The working values now were

Front Mic Boost: 21
Mic Boost: 0
Capture: 25
Capture 1: 0
Input Source: Front Mic
Input Source 1: Stereo Mixer

---

