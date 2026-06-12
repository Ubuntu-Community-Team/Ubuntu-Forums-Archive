---
title: "no sound"
date: 2010-09-09
forum: Multimedia Software
---

### Post by faraday005 on 2010-09-09
i have installed ubuntu 10.04 on HP Pavilion 1220n. There are no audio problems from the windows side but no sound from the ubuntu side.

could someone kindly help me out? i have followed all threads reporting sound problems but i was not able to fix mine from those

---

### Post by ericrcan on 2010-09-09
I was having the same problem as well for my netbook. I tried many things and I still couldnt get it to work. I finally tried this and now it works. Try this out:

Open up terminal:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

Add this at the very bottom```
options snd-hda-intel index=0 model=auto
```

Reboot, then after reboot open the terminal gain and run

```
alsamixer
```

Make sure all the volumes are turned up using the arrow keys. IF there an M at the bottom of any of them, press M to unmute it and teh M will disapear. Try that out :D

---

### Post by faraday005 on 2010-09-09
Thank you so so much, Ericrcan. You are definitely going to make me enjoy me journey with ubuntu

---

### Post by ericrcan on 2010-09-09
Glad it works. I was getting frustrated with it, so glad to know that it helped you too ):P

---

