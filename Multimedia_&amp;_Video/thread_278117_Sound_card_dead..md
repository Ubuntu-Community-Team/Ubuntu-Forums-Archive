---
title: "Sound card dead."
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by Omegabf on 2006-10-15
The only result of my attempt to get MIDI working (normal sound files played fine since install) is all sound is dead on my system.  I've tried the following to restore it:

from [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)
I used --purge to remove linux-sound-base and the alsa- packages, then reinstalled them and rebooted.  No effect.

I downloaded the alsa-source and followed the build instructions.  Result: when I tried modprobe on the driver I just got errors.

I retried the apt-get on linux-sound-base and alsa thinking I might have missed a package on the first try (didn't work this time either)

aplay -l yields:
```
aplay: device_list:221: no soundcards found...
```

lspci -v finds the card:
```
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
        Subsystem: Dell: Unknown device 0147
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at e000 [size=256]
        I/O ports at e400 [size=64]
        Memory at ee081000 (32-bit, non-prefetchable) [size=512]
        Memory at ee082000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>
```

Any thoughts? (preferably thoughts other than reinstall Xubuntu, I already have that one.)

Thanks in advance,
js

---

### Post by Omegabf on 2006-10-18
UPDATE:
I reinstalled linux, and the snd_* modules are back, but aplay still finds no sound cards.

---

### Post by Omegabf on 2006-10-18
OK, now I'm really confused:
I can hear the little sounds when the login window appears.

---

### Post by Omegabf on 2006-10-19
Nevermind.  With some help the problem was identified, my user didn't get added to the relevant groups after the reinstall.

---

### Post by tommcd on 2006-10-19
Just out of curiosity, how did you discover that your user was not in the relevant groups, and how did you add yourself.

---

### Post by Omegabf on 2006-10-19
Lots of dumb luck to figure out that was the problem (for some reason I tried "esd" and got bleeps as root or when using sudo, but not as a normal user, then Thae suggested checking a few user settings which lead to the groups).
I checked which I was in using "groups" and added the needed ones with "adduser" (after searching the forums, I found a post giving the default groups so I could set all of them)

---

