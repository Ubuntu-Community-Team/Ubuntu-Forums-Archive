---
title: "vdpau output selected, defaults to ffmpeg"
date: 2011-01-13
forum: Multimedia Software
---

### Post by roguebuck on 2011-01-13
edit: new problem since making thread title, i think ive moved in the right direction:


[[img]http://ompldr.org/tNnpiYQ[/img]](http://ompldr.org/vNnpiYQ)

i use this command:

```
mplayer -vo vdpau path/to/mkv
```

and get an error about 'vdpau cannot start: libvdpau_nvidia.so missing, no shared object exists'

how do i properly enable vdpau?

ive got a quadro nvs140m, btw.

thanks in advance!

---

### Post by roguebuck on 2011-01-14
bump, my continued search for an answer on google, here, and various other forums had yielded nothing.

---

### Post by BicyclerBoy on 2011-01-14
Have you installed libvdpau ?

Nvidia moved this out of the glx driver package & into it own...

You can find it on the nvidia vdpau ppa & elsewhere..

Run 
glxgears

post results

install vdpauinfo
run it to check working..

You are using a laptop & mobile GPU ?
You may need to adjust the BIOS & system RAM to get 512MB for the GPU.

---

### Post by BicyclerBoy on 2011-01-14
..

---

### Post by BicyclerBoy on 2011-01-14
..

---

### Post by BicyclerBoy on 2011-01-14
..

---

### Post by roguebuck on 2011-01-17
Well, i have no idea what the problem was but it seems to be outputting just fine now, and through vdpau as well. I purged all packages using 'apt-get remove --purge nvidia*', but that didnt work. I tried installing the drivers off the nvidia site multiple times, but that didnt work.

...a simple update seems to have set me straight. vdpau working as expected now...

---

