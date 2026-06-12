---
title: "Have to reinstall NVIDIA Drivers on each boot"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by ironfistchamp on 2006-11-01
Hey all

Just recently I did a fresh install of Edgy. I installed the beta NVIDIA drivers along with XGL and beryl. Now whenever I boot my machine X fails to start complaining that there is an API mismatch I believe. Something about one part of the computer saying the driver should be one version (731 4maybe?) while another says it should be the beta version. 

I would post an error log but I am unsure where it is and I can't seem to locate it. If I am informed of the location I am more than happy to post its contents.

Can anyone help me fix this annoyance?

Thanks

Ironfistchamp

---

### Post by Joe_CoT on 2006-11-01
```
sudo nano -w /etc/default/linux-restricted-modules-common
```

Change it from this:
```
DISABLED_MODULES=""
```
to this:
```
DISABLED_MODULES="nv"
```

The problem is that the linux-restricted nv module is overriding the beta nvidia kernel module. Make that change, restart, and you should be good to go.

---

