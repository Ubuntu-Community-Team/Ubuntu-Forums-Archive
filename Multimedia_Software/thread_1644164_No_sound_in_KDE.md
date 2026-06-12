---
title: "No sound in KDE"
date: 2010-12-12
forum: Multimedia Software
---

### Post by c2tarun on 2010-12-12
hi friends
i m using ubuntu Lucid on my system with KDE desktop on it.
Sometimes i dont get any sound from KDE. whenever it happens i have to open 
mixer > configure channels > then i have to select available channels as speakers and visible channels as master. after doing this i get the sound.
sometimes its bit annoying. Can anyone suggest anything

---

### Post by c2tarun on 2010-12-14
bump

i am getting this error.
the audio playback device HDA Intel (ALC269 Analog) does not work.

---

### Post by dabl on 2010-12-14
Try this: [http://ubuntuforums.org/showpost.php?p=10233536&postcount=6](http://ubuntuforums.org/showpost.php?p=10233536&postcount=6)

---

### Post by c2tarun on 2010-12-14
> **dabl said:**
> Try this: [http://ubuntuforums.org/showpost.php?p=10233536&postcount=6](http://ubuntuforums.org/showpost.php?p=10233536&postcount=6)
are you saying that i have to upgrade my distro??

---

### Post by dabl on 2010-12-14
I don't think so -- I think pulseaudio works the same in Lucid as Meerkat.

---

### Post by c2tarun on 2010-12-14
> **dabl said:**
> I don't think so -- I think pulseaudio works the same in Lucid as Meerkat.

I think
```

sudo apt-get dist-upgrade

```

is for distro upgrade

---

### Post by dabl on 2010-12-14
No, it upgrades all packages for your existing distribution and version, not to another version (you'd have to change repos, for example, to upgrade to Meerkat).

However, use ```
sudo apt-get upgrade
``` if it's more comfortable for you.  I doubt it will make any difference.

---

