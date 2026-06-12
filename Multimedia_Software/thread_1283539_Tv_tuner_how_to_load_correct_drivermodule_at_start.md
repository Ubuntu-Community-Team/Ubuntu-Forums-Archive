---
title: "Tv tuner how to load correct driver/module at startup  saa7134"
date: 2009-10-05
forum: Multimedia Software
---

### Post by DieEier on 2009-10-05
Hi all, I'm a bit of a noob so please forgive my cluelesnes. I have recently installed ubuntu 9.04 and it's awesome. Thanks to everyone involved... I hope that I can help others like this community has helped me.

Here's the prob. My tuner card used to show up as unknown/generic when using dmesg. I have succesfully watched tv by using the instruction found here [http://ubuntuforums.org/showthread.php?t=408654](http://ubuntuforums.org/showthread.php?t=408654)

My tuner works on card nr 3, but when I restart it reverts back to unknown/generic. How do I make the change permanent?

---

### Post by Jose Catre-Vandis on 2009-10-05
Have a look [here]("http://ubuntuforums.org/showpost.php?p=1946988&postcount=15")

---

### Post by sisco311 on 2009-10-05
> **DieEier said:**
> Hi all, I'm a bit of a noob so please forgive my cluelesnes. I have recently installed ubuntu 9.04 and it's awesome. Thanks to everyone involved... I hope that I can help others like this community has helped me.

Here's the prob. My tuner card used to show up as unknown/generic when using dmesg. I have succesfully watched tv by using the instruction found here [http://ubuntuforums.org/showthread.php?t=408654](http://ubuntuforums.org/showthread.php?t=408654)

My tuner works on card nr 3, but when I restart it reverts back to unknown/generic. How do I make the change permanent?

Edit /etc/modprobe.d/alsa-base.conf:
```

sudo cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf.backup
gksu gedit /etc/modprobe.d/alsa-base.conf
```

And add this line to the file:
```
options saa7134 card=3
```:

```
# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
**options saa7134 card=3**
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }

```

---

### Post by DieEier on 2009-10-05
Hi there all. Thanks for the quick response, I'm going to try right now and post back:)

---

### Post by DieEier on 2009-10-05
Thanks Sisco311 it worked first time round!!!!!! Now I just have to fig out why tv time doesn't mute sound on exit.

Once again you and Jose Catre-Vandis rock!
:guitar:

---

### Post by DieEier on 2009-10-05
If anyone else has the same sound problem then try this [http://ubuntuforums.org/showthread.php?t=281829](http://ubuntuforums.org/showthread.php?t=281829).

---

