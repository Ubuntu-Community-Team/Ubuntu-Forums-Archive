---
title: "Logitech Quickcam Messenger webcam+microphone"
date: 2008-08-06
forum: Multimedia Software
---

### Post by RedRaider1863 on 2008-08-06
Hi Everyone,

New to linux/Ubuntu. I'm running Ubuntu 8.04. I have a Logitech Quickcam Messenger, which is a USB webcam with integrated microphone.  The camera  works (using Camorama), but I can't seem to get the microphone to work. I've tried recording sound using Sound Recorder, and selecting different devices using volume control, but nothing seems to work.  Does anyone have this particular webcam working and is willing to provide some advice?  

Thanks in advance,

RedRaider

---

### Post by squaregoldfish on 2008-08-17
I've come across the same problem. Having mucked around for a while, I tried to record something in Audacity, and come up with the following error:

```
Expression 'parameters->channelCount <= maxChans' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 924
Expression 'ValidateParameters( outputParameters, hostApi, StreamDirection_Out )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1142
```

Is this of any use in figuring out what's wrong? It looks like there's something fundamentally wrong in the camera's parameters - my guess would be an unitialised value for channelCount, but I'm no expert.

Steve.

---

