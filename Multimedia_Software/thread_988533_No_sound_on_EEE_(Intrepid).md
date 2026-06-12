---
title: "No sound on EEE (Intrepid)"
date: 2008-11-20
forum: Multimedia Software
---

### Post by rich.bradshaw on 2008-11-20
Hi,

Having migrated to stock Ubuntu on my EEE 701, the sound doesn't work at all. Instead I get a mild crackling when I try to play any sound.

I've just got the stock system + the array kernel.

Any ideas?

---

### Post by aysiu on 2008-11-20
Maybe it's a bug?
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/220842](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/220842)

---

### Post by rich.bradshaw on 2008-11-23
No it's not that - just get crackling when playing and sound no matter which audio is used. (alsa or pulse)

---

### Post by psyke83 on 2008-11-23
> **rich.bradshaw said:**
> No it's not that - just get crackling when playing and sound no matter which audio is used. (alsa or pulse)

Don't dismiss that bug so easily. Many users are experiencing a bug in Intrepid where their PCM mixer gets muted without user intervention - crackling sound and the PCM mixer muting itself are both separate (though related) bugs.

Check your PCM mixer (but you must specify your hardware sound card explicitly in Intrepid, this may be causing confusion):

```
$ alsamixer -Dhw
```

---

### Post by rich.bradshaw on 2008-11-23
> **psyke83 said:**
> Don't dismiss that bug so easily. Many users are experiencing a bug in Intrepid where their PCM mixer gets muted without user intervention - crackling sound and the PCM mixer muting itself are both separate (though related) bugs.

Check your PCM mixer (but you must specify your hardware sound card explicitly in Intrepid, this may be causing confusion):

```
$ alsamixer -Dhw
```


Ah, can't believe I hadn't checked that! Sound output on the EEE is PCM, not master.

Think that I'd read lots of others having problems and had assumed that they had all checked the obvious...

---

