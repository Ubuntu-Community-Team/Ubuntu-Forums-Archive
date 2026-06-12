---
title: "Speakers Crackling"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by Fayte2071 on 2007-06-06
For some reason, on my linux side (I dual boot windows and linux) whenever i play music, or something certain sounds in general, my speakers are like...crackling... I thought it was that my speakers were blown, but I went to my windows side and played music and such; The speakers didn't crackle. Are there some settings i need to configure for this?

---

### Post by dilb on 2007-06-06
I had the same problem, and found that adjusting the volume controls removed the cracking. I seem to remember it was Aux or Aux 2 causing the problems. I know that sounds amazing patronising, but honestly, I would tinker with the volume settings first. Don't forget some of the controls aren't visible unless you select them in the preferences. Good luck!

---

### Post by eggdeng on 2007-06-06
```
cat /proc/asound/cards
``` to see if you are using the VIA 8233 chip. If so, the fix is posted at [http://ubuntuforums.org/showthread.php?t=398599](http://ubuntuforums.org/showthread.php?t=398599)

---

### Post by mlind on 2007-06-06
If you're using feisty, There are couple of related bugs in launchpad.net about this issue
[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/97004](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/97004)
[https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/103025](https://bugs.launchpad.net/ubuntu/+source/alsa-lib/+bug/103025)
[https://bugs.launchpad.net/mplayer/+bug/85751](https://bugs.launchpad.net/mplayer/+bug/85751)

I'm suspecting a bug in alsa-lib, but no one has yet confirmed this. For me, the issue was solved by rebuilding alsa-lib with certain patch disabled.

---

### Post by ataxicwolf on 2008-01-15
I had the same problem with speakers crackling in Fiesty. The solution was to go into my volume settings, go to preferences, and change it to an OSS mixer.

---

### Post by mlind on 2008-01-16
> **ataxicwolf said:**
> I had the same problem with speakers crackling in Fiesty. The solution was to go into my volume settings, go to preferences, and change it to an OSS mixer.

The bug that you're experiencing is probably this [https://bugs.edge.launchpad.net/ubuntu/+source/alsa-lib/+bug/116990](https://bugs.edge.launchpad.net/ubuntu/+source/alsa-lib/+bug/116990). It was fixed only since Gutsy though.

---

