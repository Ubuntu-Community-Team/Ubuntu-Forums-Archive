---
title: "Trouble with Cam and Module gspca not found."
date: 2009-07-02
forum: Multimedia Software
---

### Post by Glen Darby on 2009-07-02
Hi,
Been trying to install the webcam Creative PD0040
I seem to have it working 
```
glen@glen-desktop:~$ sudo lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04b8:080e Seiko Epson Corp. CX-3500/3600/3650 MFP
Bus 001 Device 002: ID 05a9:0518 OmniVision Technologies, Inc. OV518 WebCam
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
But it keeps coming up with Error :-
could not connect to video device (/dev/video0)

When I check with grep -- 
```
glen@glen-desktop:~$ sudo lsmod | grep -i gspca
```
There are no results.

When I check the gspca its not found --
```
glen@glen-desktop:~$ sudo modprobe gspca
FATAL: Module gspca not found.

```

Ive also tried a build, but nothing is in the directory --
```
glen@glen-desktop:~$ ./gspca_build
bash: ./gspca_build: No such file or directory

```

Anyone got any clues?

Thanks ... Glen.
FATAL: Module gspca not found.

---

### Post by entropic_existence on 2009-07-03
I've been having the same problems with mine. I have the LPIA kernel, not sure if that makes any difference. I did have gspca_sources downloaded so I was able to try and build it in that directory but there are problems building it because of  changes made to the kernel and gspca_sources not being up to date.

---

