---
title: "Video card for HDMI w/ working audio"
date: 2010-01-26
forum: Mythbuntu
---

### Post by Amorget on 2010-01-26
I currently have a brand newly built HTPC running 9.10 64bit, a Biostar G41 DVI motherboard w/ Intel C2D proc and a MSI 9400 passively cooled video card.  It is awesome because it is nearly silent.... however that continues on to the audio output through HDMI.  I cannot get it to work, however it does work in Windows 7 but I am not going that route.

Can anyone recommend a HDMI option that will for sure work?  As I understand the ATI cards have their own built in audio device and while I prefer Nvidia I will buy an ATI if it will work with minimal issues.  The new Nvidia cards also seem to have built in Audio, however I've read that they still down work with Ubuntu.

Thanks,
Douglas

---

### Post by LowSky on 2010-01-26
If your using the restricted driver it should by now, older version had problems But I believe all was fixed aroun 8.10.

Go to sound preferences and choose HDMI for output, that should do it.

---

### Post by Amorget on 2010-01-26
> **LowSky said:**
> If your using the restricted driver it should by now, older version had problems But I believe all was fixed aroun 8.10.

Go to sound preferences and choose HDMI for output, that should do it.

I wish it was that easy.  There is no HDMI output listed anywhere.

[http://ubuntuforums.org/showthread.php?t=1387108](http://ubuntuforums.org/showthread.php?t=1387108)

There is my thread on trying to get the HDMI audio working.

---

### Post by LowSky on 2010-01-26
Try what thhis guy suggests, he used a Nvidia 8800 and routed the onboard sound to passthrought the HDMI, try that maybe... heres the link

[http://ubuntuforums.org/showthread.php?t=967023](http://ubuntuforums.org/showthread.php?t=967023)

---

### Post by Amorget on 2010-01-26
Any idea what the equilivant to System -> Preferences -> Sound is in Mythbuntu?

---

### Post by LowSky on 2010-01-26
sorry so used to gnome, try opeing terminal and typeing

xfce4-mixer

,more info in this link
[http://ubuntuforums.org/showthread.php?t=1130885](http://ubuntuforums.org/showthread.php?t=1130885)

---

### Post by Amorget on 2010-01-27
Hi,
The xfce4-mixer isn't really equal to the Sound Preferences from what I can tell.  It doesn't give me any option to pick Digital out or anything.

If I run speaker-test -c 2 -D plughw:0,1 (I only have 0,0 or 0,1) it doesn't error, however I still get no sound.

Thanks,
Douglas

---

### Post by Amorget on 2010-01-28
Well, I installed Ubuntu 9.10 on it and guess what, all the directions work to get HDMI working!  Took me 15 minutes...

So, it is something specific to Mythbuntu...

---

