---
title: "No Sound on Fiesty SB450 HDA ATI (Intel HDA Driver)"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by Bastien on 2007-05-01
Hi everyone!

I just passed from the Edgy Eft to Fiesty and I was very disapointed not hearing the drums at startup.
At first I though it was just normal but when I wanted to check if the system sounds were working well I couldn't hear anything...

What IS surprising is that on previous versions my card was unknown. But it DID work very well...
ALSA was something named 'Generic' and it worked well.
Now it is recognized ie I can see the name of my device, but ... no sound.
Here are screenshots of what the hardware manager says:
[IMG]http://img510.imageshack.us/img510/3325/screendevicemanagerqf6.jpg[/IMG]

PS: I already checked that Sound is not muted nor down to 0. My phones are ON (actually its a laptop so its always on). And I'm pretty sure I checked all the silly things.

I'd really like somebody to help me!
Note that I'm a beginner and that if you tell me to do some things please make it clear and as detailed as possible.

Bastien.

---

### Post by anirban.sam on 2007-05-05
Type alsamixer and press enter in a console to launch alsamixer. Disable all ICE devices in alsamixer and unmute all muted. Save settings by typing "sudo alsactl store".

---

