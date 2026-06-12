---
title: "Very Poor nvidia Performance!"
date: 2008-10-20
forum: Multimedia Software
---

### Post by Del Piero on 2008-10-20
Alright i have been browsing different forums the whole day trying to find out a way to increase my World Of Warcraft FPS using Cedega and D3D and during that quest i found out that the problem might have to do with the nvidia drivers on my ubuntu (Linux Mint). Anyway here are my system specs:

agp_aperture_size: 188
cpu: Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu_ghz: 2.99
distro: Ubuntu 8.04 hardy
kernel: 2.6.24-16-generic
machine_bitness: 32
memory: 1518
soundcard: Cirrus Logic CS4281 at 0xfeafe000, irq 17
soundcard_driver: ALSA Version 1.0.16
videocard_direct: True
videocard_driver_version: 2.1.2 NVIDIA 169.12
videocard_manufacturer: NVIDIA Corporation
videocard_ram: 256
videocard_type: GeForce 6200/AGP/SSE2
x_version: X.Org X Server 1.4.0.90
GUI version: 000133

And here are the results i get when i run glxgears in a terminal

6012 frames in 5.0 seconds = 1202.372 FPS
6127 frames in 5.0 seconds = 1225.371 FPS
6117 frames in 5.0 seconds = 1223.247 FPS
6141 frames in 5.0 seconds = 1228.200 FPS
6120 frames in 5.0 seconds = 1223.732 FPS
6206 frames in 5.0 seconds = 1241.053 FPS


Compared to what i saw today posted by people with lesser systems/cards it's extremely low, anyway i would appreciate it very much if someone takes time to work that performance issue with me or at least tell me whats going on, thanks.

---

### Post by Del Piero on 2008-10-21
Installed Envy drivers and nothing happened, removed and switched back to the Ubuntu drivers and still stuck with this poor performance problem.

---

### Post by sandy8925 on 2008-10-21
might have something to do with your soundcard

---

### Post by Del Piero on 2008-10-21
> **sandy8925 said:**
> might have something to do with your soundcard

how come?

---

### Post by Del Piero on 2008-10-21
Can someone please elaborate what he meant?

---

### Post by Del Piero on 2008-10-21
One would've thought that with more people they'd get more help, i really hate to say this but this community is becoming less and less helpfull as the days passes by.

---

### Post by maximAL on 2008-10-31
i got the same problem as Del Piero. recently i noticed that my 3D performance is pretty poor, so i ran glxgears and got about ~3500FPS.
i had the nvidia-glx-new version 169.12 installed and then switched to nvidia-glx-new-envy version 173.14.12. unfortunately, glxgears dropped to ~2500FPS now :(
graphics card is a 8800GT. i also got a dual monitor TwinView configuration - thats why i don't want to manually install the latest-and-greatest driver by hand, as setting up twinview proved to be a pain in the **** in the past.

---

