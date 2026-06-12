---
title: "Usb webcam built in mic makes me sound like a mouse."
date: 2009-04-30
forum: Multimedia Software
---

### Post by Kristofer Gustafsson on 2009-04-30
I found my old webcam today and decided to plug it in and it worked without any problems, sure it's old and video was super bad quality but i needed a mic. When i try to use it in any application like sound recorder it makes my voice very .. Not pitched it's actually sped up.. I talk really fast on playback, it's super strange :P Even when making skype test call.

If i go into sound devices it tells me it's a OmniVision Technologies, inc USB Camera.

---

### Post by markbuntu on 2009-05-01
Sounds like the wrong sample rate is being used. Check in your syslog or messages for something like this

Apr 25 19:21:20 mark386-desktop pulseaudio[8878]: alsa-util.c: Device hw:3 doesn't support 44100 Hz, changed to 16000 Hz.
Apr 25 19:21:20 mark386-desktop pulseaudio[8878]: alsa-util.c: Device hw:3 doesn't support 2 channels, changed to 1.

---

### Post by Kristofer Gustafsson on 2009-05-02
I think this might be something.

May  2 10:49:58 starman pulseaudio[11212]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
May  2 10:49:58 starman pulseaudio[11212]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May  2 10:49:58 starman pulseaudio[11212]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer

Can i try another sample rate somehow? By the way, thanks for the reply i thought my thread was dead. :)

---

### Post by markbuntu on 2009-05-03
A lot of webcams use 8000hz sampling rate. How you sould change that as a default I am not sure but it is probably what you are up against.

---

