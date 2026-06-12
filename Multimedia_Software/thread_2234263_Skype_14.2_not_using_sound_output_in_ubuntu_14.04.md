---
title: "Skype 14.2 not using sound output in ubuntu 14.04"
date: 2014-07-13
forum: Multimedia Software
---

### Post by ubifree on 2014-07-13
Skype 14.2 is not using my speakers for voice output. My speakers work fine when using RhythmBox and I hear the ring call when someone's calling me on Skype. They can hear me but I can't hear them!  I hear no sound when I call the Echo/Sound Test service. Skype worked fine (apart from the odd crash) in ubuntu 12.04 but I've had no sound output since I upgraded to 14.04. This Skype was installed from the Canonical Partner repositories in the Ubuntu Software Centre and is v4.2.0.11.

Can someone please suggest how to fix this?  I've installed pavucontrol as I've seen some people recommend, and also reinstalled Skype, but this has not cured the issue.  I've also tried installing a later version of Skype from Skype's website but that didn't fix it either so I went back to the 4.2 from the Ubuntu Software Centre.

---

### Post by ubifree on 2014-07-29
In case it helps anyone else I managed to get sound output back in Skype by starting pavucontrol *whilst Skype was running (calling the Echo service)*.  Skype then appears as an application in the Playback tab of pavucontrol. For some reason the audio had been muted, so clicking on the icon of the microphone unmuted it and I got sound back!  But Skype must be attempting to output audio at the time you are looking at the Playback tab in pavucontrol; otherwise you won't see it.

However, I still sounded crackly to other people I was Skyping with.  That was fixed by uninstalling and reinstalling Skype from a terminal:
```
sudo apt-get autoremove --purge skype[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]sudo apt-get update
sudo apt-get install skype
```

---

