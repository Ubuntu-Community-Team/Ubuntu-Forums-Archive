---
title: "Extremely loud headphones, decreasing volume gain in alsamixer does not persist"
date: 2020-06-11
forum: Multimedia Software
---

### Post by postcd on 2020-06-11
Hello,

on my computer with Ubuntu 16.04.6 LTS, 4.4.0-180-generic is extremely loud headphones audio output.
When i decrease headphone volume in alsamixer command line utility from gain 0 db to minimum gain available (-45,00db) and quit it, then the volume is acceptable. But later i always find it reseted back to gain 0.00db. How to set decreased headphones volume permanently?

Card: Intel 82801DB-ICH4
Chip: SigmaTel STAC9750,51

---

### Post by CatKiller on 2020-06-11
It's possible that you've got "flat volumes" enabled.

>        flat-volumes=  Enable  'flat' volumes, i.e. where possible let the sink
       volume equal the maximum of the volumes of the inputs connected to  it.
       Takes a boolean argument, defaults to yes.

Because of that, applications can set the volume to 100% without meaning to. That "defaults to yes" was eventually changed to "defaults to no," but your system may well be from before that change.

It's a setting in /etc/pulse/daemon.conf. I don't know if it's exposed anywhere else.

---

### Post by postcd on 2020-06-12
Thanks, i installed the system several years back. Based on your comment, i did following:

$ grep -i flat /etc/pulse/daemon.conf
flat-volumes = no

$ sed -i "s/flat-volumes = no/flat-volumes = yes/g" /etc/pulse/daemon.conf

$ grep -i flat /etc/pulse/daemon.conf
flat-volumes = yes

I hope that is all that was needed. I will report back if the problem continue.

---

### Post by postcd on 2020-06-14
Today i see again in alsamixer the headphone volume was reseted again, so problem continue... Note that i have not restarted computer or any service yet.

---

### Post by Yellow Pasque on 2020-06-14
You haven't rebooted in two days? You need to at least restart pulseaudio for the change(s) to take effect. Logging out and in is the easiest way, but you can force a restart/respawn:
```
pulseaudio -k
```

---

### Post by postcd on 2020-11-29
Even after reboot problem is there. Volume is reseted from my setting -45.00db back to 0 which means very loud that i get shock when the sound plays. Please kindly send me more ideas on what to try to set permanent volume or try to fix or debug this.

---

### Post by Yellow Pasque on 2020-12-02
The best way to do this would be to make an amixer command and run it at startup.
```
man amixer
```

---

### Post by postcd on 2020-12-03
> **Yellow Pasque said:**
> make an amixer command and run it at startup.
```
man amixer
```

Thanks, but i do not think this can be the solution since the sound volume is reset during the login session, so i would have to run it every minute to minimize chances of hearing maxed out sounds. If that amixer command would work.

---

