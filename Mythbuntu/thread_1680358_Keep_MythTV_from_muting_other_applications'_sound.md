---
title: "Keep MythTV from muting other applications' sound?"
date: 2011-02-02
forum: Mythbuntu
---

### Post by Lido on 2011-02-02
I use my computer for MythTV mostly, but also sometimes use other applications. Some of those applications should output sound, but as long as the frontend application is running, they're all muted. I've looked through all the MythTV front and backend setup options, but can't find a way to disable this. Is it possible? I'm not familiar with command-line flags for myth, but maybe that would be the way to do it. Thanks.

---

### Post by AKADAP on 2011-02-02
Pulse audio is required to allow simultaneous sound from multiple applications. By default MythTV disables Pulse Audio. You need to manually select pulse audio in MythTV for simultaneous sound to work. If you are using digital pass thorough, selecting pulse audio in MythTV will disable digital pass through.

---

### Post by thatguruguy on 2011-02-02
> **AKADAP said:**
> Pulse audio is required to allow simultaneous sound from multiple applications. By default MythTV disables Pulse Audio. You need to manually select pulse audio in MythTV for simultaneous sound to work. If you are using digital pass thorough, selecting pulse audio in MythTV will disable digital pass through.

As of .24, I don't believe that MythTV still disables pulse audio by default.

---

### Post by Lido on 2011-02-13
I'm using 0.23 fixes (26437) according to the frontend info center. I looked in setup but don't see any place to enable pulse audio. My audio output is set to "Alsa: default" in the general settings in the front end and I have an analog speakerwire going from the speaker port on the myth box to the analog input on the TV.

---

### Post by AKADAP on 2011-02-13
> **Lido said:**
> I'm using 0.23 fixes (26437) according to the frontend info center. I looked in setup but don't see any place to enable pulse audio. My audio output is set to "Alsa: default" in the general settings in the front end and I have an analog speakerwire going from the speaker port on the myth box to the analog input on the TV.

Did you hit the "Scan" button on the audio setup page? The list of options will not be populated until you do.

---

### Post by nickrout on 2011-02-13
> **AKADAP said:**
> Did you hit the "Scan" button on the audio setup page? The list of options will not be populated until you do.

He is running 0.23, the scan option is in 0.24 and above.

If the OP wants pulse audio output options in myth, he will have to update.

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

---

