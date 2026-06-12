---
title: "No Sound On Mythtv Frontend PVR-500mce"
date: 2008-04-30
forum: Mythbuntu
---

### Post by taehC on 2008-04-30
Please help!
I know my sound can work because I can play a movie in vlc outside of mythtv, but when I am watching tv on my frontend, then there is no sound, just video.  Can anyone help?  I am using a pvr-500 mce dual tuner card.
And yes, the volume is turned up...

---

### Post by natrixgli on 2008-04-30
I notice that if I've got firefox open and have been watching vids on YouTube, I have to close it for Myth's sound to work. I can probably solve this, but it's not a priority..

You might check your default sound device in the Mythfrontend Setup > General

Cheers,

-n8

---

### Post by taehC on 2008-04-30
what sound device should i have it set to? there are like 10 of them or so.  should i just try each one?

---

### Post by taehC on 2008-05-02
can anyone help?

---

### Post by Chuckels550 on 2008-05-02
In my experience there are two places you need to look at to ensure you get sound in MythTV.  The first is in the MythTV Frontend>General - go to the Audio page.  Audio output device  - try ALSA:Default and Passthrough Output Device: try default. 

The other is the Alsamixer that is best managed through a terminal window with the command alsamixer.  In alsamixer ensure that nothing you use is muted and if you use analog sound, that the Digital/Audio Line-In/Out Jack is not enabled.

Anyway, you will need to play with these audio controls to ensure that the audio works for your set-up.

---

### Post by taehC on 2008-05-13
ok when i try to watch tv on my frontend machine in terminal, it says
```
mixer unable to find control Master 1
```
does this help?
also i have found another problem...
when i plug a moniter into my backend and try to watch tv on it, there is also no sound!  can anyone help?  this is really starting to worry me!

---

### Post by taehC on 2008-05-15
can anyone help?

---

### Post by taehC on 2008-05-16
is there any other info i can gather to help anyone out?

---

### Post by taehC on 2008-06-09
ok now all of a sudden, no video that has is on my hard drive can play with sound... i can still play video on my windows partition, but no sound for video in linux off of the hard drive, on the net video does work.

---

### Post by pipenew on 2008-06-29
I had the same problem and realized that the volume resets to 70% which for some reason is already too low for my speakers to get the sound.

Does anybody know how to configure mythtv to start at a certain volume?

Thanks

---

