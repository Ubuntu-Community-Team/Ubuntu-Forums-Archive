---
title: "Audio problems!"
date: 2008-08-13
forum: Multimedia Software
---

### Post by bambinn on 2008-08-13
Hi guys,
i have a problem with the audio, its probably related to the fact that im a noob in Linux.
i recently installed Ubuntu and all drivers work fine including the Soundcard Driver. The driver is for a Delta 1010LT soundcard,

when im on youtube and other similar pages the sound works fine, no problems..  but when i open a mp3 or a video file (not on the web), the sound doesn't work! video works fine but no sound! ive tried vlc player and a few other players, and it doesn't work. 

HELP!

---

### Post by Raffles10 on 2008-08-13
I'm new to Ubuntu as well. 

I had sound problems until I found the following "How To" and since following all the steps I've had no problems:

[The (almost) Perfect Pulse Audio Setup]("http://ubuntuforums.org/showthread.php?t=776739")

---

### Post by trevelyan on 2008-08-13
type this in a terminal:
```

sudo killall pulseaudio

```
that should do it.

---

### Post by bambinn on 2008-08-13
nope, neither worked!! i installed Pulseaudio and still no sound, the command didn't work either..!

---

### Post by markbuntu on 2008-08-13
Go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

