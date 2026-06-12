---
title: "skype is driving me mad...then ubuntu hardy"
date: 2009-05-03
forum: Multimedia Software
---

### Post by viaciofano on 2009-05-03
as you can see i am struggling with ubuntu. i have only started using this year and thought it brilliant but as i have to learn the system i have upgraded in the past and found issues with monitor resolution etc. now that is all sorted i am having issues with skype. only yesterday it worked. now i have not upgraded or changed any settings. talked to a friend yesteday and it worked. today no success at all.
can anyone help me with a flow chart to try and succeed..
Vinny

---

### Post by xc3RnbFO8P on 2009-05-03
Try to run Skype from Terminal and see if you get some errors report.

---

### Post by viaciofano on 2009-05-03
i can get skype the program to start up but
just now i load skype, try a test call and get  
problem with audio playback
i can change the settings but do not get skype to either record my voice, even though earlier yesterday it worked fine. now no sound on playback or will it record my voice. i can chat to others on skype ok. so i guess the program is ok and that my settings possibly on the sound card are dodgy?
Vinny

---

### Post by xc3RnbFO8P on 2009-05-03
> i can change the settings but do not get skype to either record my voice, even though earlier yesterday it worked fine. now no sound on playback or will it record my voice. i can chat to others on skype ok. so i guess the program is ok
Yes that's strange.

---

### Post by viaciofano on 2009-05-03
sorry i meant that i can chat to others by typing comments not speaking. the program itself i guess is ok. i have a hunch it could be usb related or changing the paths that the program uses for microphones etc

---

### Post by xc3RnbFO8P on 2009-05-04
First install **skype-common** if you haven't.

---

### Post by viaciofano on 2009-05-04
i haven't installed and have checked on synaptic package manager and it is not installed. 
can i install the pro gramme while skype is installed?

---

### Post by xc3RnbFO8P on 2009-05-04
> can i install the pro gramme while skype is installed?
Yes

---

### Post by viaciofano on 2009-05-04
sorry no go..it wont let me upload as the package.....crashes

E: /var/cache/apt/archives/skype-common_2.0.0.72-0medibuntu4_all.deb: trying to overwrite `/usr/share/skype/sounds/CallFailed.wav', which is also in package skype

---

### Post by xc3RnbFO8P on 2009-05-04
Try to uninstall skype and install it again.

---

### Post by DeadlyAura on 2009-05-04
I had this same problem. Does audio playback fail? or can you not hear your own voice?

If there is a problem with playback, simply pick different drivers until you find the ones that will successfully place a call. Make sure you use the same drivers for both recording and playback otherwise it will always fail.

Once you can place a call successfully, check your system volume settings. It is common that the microphone will mute itself in the system volume settings. Unmute the mic and play with the volume levels and boost levels until you can hear your voice. Be careful though because turning the mic volume or mic boost up too high will cause your voice to be picked up above the volume threshold. If this happens, even though your mic is on, you will not hear your own voice as it will not be recorded due to the extreme volume.

best of luck.

---

