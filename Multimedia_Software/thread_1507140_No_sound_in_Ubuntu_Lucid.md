---
title: "No sound in Ubuntu Lucid"
date: 2010-06-11
forum: Multimedia Software
---

### Post by Badbunny on 2010-06-11
I assume this has been answered before, but I couldn't find a working solution.
So, I just did a fresh install of Ubuntu 10.04 and I have no sound. Every app seems to play music just fine, but I can't hear anything.
I can hear dogs barking outside, so it's not me.
I checked alsamixer for muted channels, but no luck.
Alsactl init gives me
```
Unknown hardware: "HDA-Intel" "Analog Devices AD1988" "HDA:11d41988,104381e1,00100400" "0x1043" "0x81ec"
Hardware is initialized using a guess method
```
Any help would be appreciated, since the dogs are really getting to me.

---

### Post by Badbunny on 2010-06-12
I re-installed Ubuntu last night, having this naive wish that it would help. Now alsactl init gives me:
```
alsactl: init:1743: No soundcards found...
```

Needless to say, I still have no sound. Any ideas?

---

### Post by Badbunny on 2010-06-12
An update: 
I installed "linux-backports-modules-generic" and now I'm back to 
```
Unknown hardware: "HDA-Intel" "Analog Devices AD1988" "HDA:11d41988,104381e1,00100400" "0x1043" "0x81ec"
Hardware is initialized using a guess method
```

Sound is still consistently absent.

---

### Post by Badbunny on 2010-06-13
I followed the ubuntu sound troubleshooting guide as good as I understood it, but it didn't help. It got me this website: [http://www.alsa-project.org/db/?f=fb2ab2d7a2c59f7dc8c5e28e94c893b36815ca34](http://www.alsa-project.org/db/?f=fb2ab2d7a2c59f7dc8c5e28e94c893b36815ca34) , if that's any help to anyone trying to help. 

Anyone?

---

### Post by ekseniks on 2010-06-13
I had the same problem but mine was due to the NVIDIA drivers I installed for my gfx card, uninstalling the drivers brought back the sound but lost the desktop effects, after much faffing, i tried again a few days later and it all worked.
 
Sorry I only realised half way through this that its not helping :/
 
Good luck!

---

### Post by Badbunny on 2010-06-13
Now it works. 

I have no idea what I did, but I assume the problem was with pulseaudio settings, as I was horsing around with them just before the sounds came back after a reboot.

Well, as long as it works... :guitar:

---

