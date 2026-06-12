---
title: "[NVIDIA]API version mismatch"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by supertux on 2007-04-20
Hi,

i have a problem with the nvidia-glx drivers for my geforce ti4800.. When i start X  i get the message API version mismatch. In the search i found a thread with a workaround for it:

[I]API version mismatch upon loading gdm.

I gotta CTRL+ALT+F1
then I type

sudo killall gdm
sudo modprobe -r nvidia
sudo modprobe -i nvidia
sudo gdm

and i'm able to load up gdm and conversely X with the modules loaded properly.
The issue is, why is it using the wrong module on loading?

it's annoying to have to do this every time I restart my computer.[/I]

is there any way to get rid of this workaround ?

---

