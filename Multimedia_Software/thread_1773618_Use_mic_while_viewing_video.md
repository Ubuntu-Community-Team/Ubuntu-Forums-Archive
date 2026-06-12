---
title: "Use mic while viewing video"
date: 2011-06-02
forum: Multimedia Software
---

### Post by tripler on 2011-06-02
I'd like to use my mic to talk over the soundtrack of an avi (viewed on VCL). I'm running uhuntu 9.10 netbook edition on an eeepc PE.

Is this possible?

Thanks

---

### Post by johngreth on 2011-06-02
I don't see why it wouldn't work. Does the microphone work when you aren't playing a video?

---

### Post by tripler on 2011-06-02
No, the mic doesn't work while playing an avi (using VLC).

In fact I don't know of an app on ubuntu which amplifies the mic. I can record through the mic with Sound Recorder and it plays back ok (but doesn't amplify during the recording). Skype amplifies the mic but only during a skype call.

Thanks for any help.-

---

### Post by johngreth on 2011-06-02
A while ago I noticed that when I was using skype the volume on the mic automatically turned down when I got too close. Maybe your system is doing the same, except actually turning it off.
Anyway, what is your end goal. I don't really understand what you are trying to achieve.

---

### Post by tripler on 2011-06-02
I want to be able to hear my own voice over the speakers at the same time as the sound from an avi I'm watching.

---

### Post by johngreth on 2011-06-02
I was sort of able to get it working with 
```
pacat -r | pacat -p
```
but there is so much lag it isn't really useful. It basically takes the input stream and loops it back to the output stream. I'm not sure if it will work with another playback going at the same time.

---

