---
title: "bad resolution for full screen apps"
date: 2008-04-21
forum: Multimedia Software
---

### Post by mad_hatter5 on 2008-04-21
When I run any full screen applications (usually games), the screen flashes black but then windows the application instead. When I press alt-enter nothing changes, and it says that it is in full screen mode when its clearly windowed. I assume Ive got something wrong with my xorg.conf or my driver set up. Im using an Nvidia Geforce2 Go with the default drivers enabled in restricted Drivers manager. When I lsmod though, there arent any drivers listed next to nvidia.

---

### Post by mastermindg on 2008-06-07
I'm using the GeForce 8500GT on my system and after reading a bunch of guides I figured out the easiest thing was just to use nvidia-settings.

If you don't have it installed (I didn't initially, even after the glx driver install) install it from synaptic.

---

