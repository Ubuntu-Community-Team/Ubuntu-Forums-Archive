---
title: "Hardware Drivers doesn't download"
date: 2010-04-02
forum: Multimedia Software
---

### Post by emaloli on 2010-04-02
hi, I just installed ubuntu 9.10 32bit on my compaq 6000.

I have a  nVidia Corporation NV17 [GeForce4 MX 420] graphic card, and I wanted to install the proper drivers.

I tried to use Hardware Drivers, but when it tries to activate the "NVIDIA accelerated graphic ... ... (version 96)", it starts a download and then it simply stops doing anything.

I also tried to use EnvyNg, which also started downloading and stopped.

I also tried to install manually the "NVIDIA-linux-x86-96.43.01-pky1.run" (which was what Envy recommended) but

1) I'm a Noob and most forums said "don't mess with your graphic card if you're not confindent enough"

2) when I do

sudo /etc/init.d/gdm stop
sudo sh NVIDIA-linux-x86-96.43.01-pky1.run

it says that I don't have a precompiled kernel interface, and something about kernel sources not matching current kernel (but "gcc -dumpversion" shows the same as "cat /proc/version").

Any suggestions? Thanks!

---

### Post by emaloli on 2010-04-02
Solved

I found that there was a more recent version of the driver x86-96.43.16 and installed that manually.

---

