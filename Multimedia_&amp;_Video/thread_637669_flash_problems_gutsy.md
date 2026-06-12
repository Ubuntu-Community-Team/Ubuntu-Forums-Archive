---
title: "flash problems gutsy"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by nalleballe on 2007-12-11
Hi folks. Im hoping for some help here. Im stuck on flash installment. Whenever im staring Mozilla (or any browser) im promped to install flash or gnash. Here is the deal: When i try to install the nonfree adobe flash i get the message thats already installed. When i install gnash it all hangs to the point of rebooting the system. (garbage) So i open the Synaptic and uninstalls the both. I then download the adobe flash from thier homepage and this is what i get:

root@nat-desktop:/home/nat/Skrivbord# rpm -Uvh flash-plugin-9.0.115.0-release.i386.rpm 
fel: Ouppfyllda beroenden:
        /bin/bash behövs av flash-plugin-9.0.115.0-release.i386
        /bin/sh behövs av flash-plugin-9.0.115.0-release.i386
        libX11.so.6 behövs av flash-plugin-9.0.115.0-release.i386
        libXext.so.6 behövs av flash-plugin-9.0.115.0-release.i386
        libXt.so.6 behövs av flash-plugin-9.0.115.0-release.i386
        libc.so.6 behövs av flash-plugin-9.0.115.0-release.i386
        libc.so.6(GCC_3.0) behövs av flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.0) behövs av flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.1) behövs av flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.1.3) behövs av flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.2) behövs av flash-plugin-9.0.115.0-release.i386
        libc.so.6(GLIBC_2.3) behövs av flash-plugin-9.0.115.0-release.i386
        libdl.so.2 behövs av flash-plugin-9.0.115.0-release.i386
        libdl.so.2(GLIBC_2.0) behövs av flash-plugin-9.0.115.0-release.i386
        libdl.so.2(GLIBC_2.1) behövs av flash-plugin-9.0.115.0-release.i386
        libfontconfig.so.1 behövs av flash-plugin-9.0.115.0-release.i386
        libfreetype.so.6 behövs av flash-plugin-9.0.115.0-release.i386
        libglib-2.0.so.0 behövs av flash-plugin-9.0.115.0-release.i386
        libgobject-2.0.so.0 behövs av flash-plugin-9.0.115.0-release.i386
        libgtk-x11-2.0.so.0 behövs av flash-plugin-9.0.115.0-release.i386
        libm.so.6 behövs av flash-plugin-9.0.115.0-release.i386
        libm.so.6(GLIBC_2.0) behövs av flash-plugin-9.0.115.0-release.i386
        libpthread.so.0 behövs av flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.0) behövs av flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.1) behövs av flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.2) behövs av flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.2.3) behövs av flash-plugin-9.0.115.0-release.i386
        libpthread.so.0(GLIBC_2.3.2) behövs av flash-plugin-9.0.115.0-release.i386
root@nat-desktop:/home/nat/Skrivbord# rm ~/.mozilla/firefox/*.default/xpti.dat
root@nat-desktop:/home/nat/Skrivbord# 

oh sorry its swedish but it all is unfofilled deps... How in the hell can Synaptic install flash nonfree (same) without these deps? and how will i get my deps in place? and how will i get a working flash? any ideas? MANY THANX IN ADVANCE

---

### Post by Bablefish on 2007-12-11
have you honesty checked out Add Remove? It's listed there.

---

