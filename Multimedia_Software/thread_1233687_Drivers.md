---
title: "Drivers"
date: 2009-08-07
forum: Multimedia Software
---

### Post by JustinoLatino on 2009-08-07
I'm sorry if this is posted in the wrong section but it seemed fitting. I have a Compaq Presario F700 and I need a video driver. The only reason I need a driver is because I have a massive crack in my on board screen so I use a monitor, Linux doesn't detect the second monitor and it only displays in 800x600 max on a 16 in monitor which is quite annoying. And I don't know about the community here since I'm new but please don't say "OMG GOOGLE IT NOOB!!!1111!!!" Because I did and got fed up and decided to ask you all for help. Thanks in advance. The graphics card is an Nvidia GeForce 7000M bye the way with x64 ubuntu.

---

### Post by HappyFeet on 2009-08-07
Just go to System>Administration>Hardware Drivers and install the Nvidia driver.

Then do
```
gksudo nvidia-settings
```
to configure the settings.

---

### Post by abelbrito on 2009-10-03
i have the same problem.
i just installed Ubuntu 9 on my Presario F700. thing is, the hardware drivers don't show me any Nvidia drivers. how do i install these?
thanks in advance

---

### Post by beastrace91 on 2009-10-03
Go download the driver for your system arch:

[32bit nVidia 185.18.36 Download](ftp://download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run)

[64bit nVidia 185.18.36 Download](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.36/NVIDIA-Linux-x86_64-185.18.36-pkg2.run)

Then for installing follow the directions found [here](https://help.ubuntu.com/community/NvidiaManual)

Have any questions/issues feel free to let me know,
~Jeff

---

### Post by abelbrito on 2009-10-04
> **beastrace91 said:**
> Go download the driver for your system arch:

[32bit nVidia 185.18.36 Download]("ftp://download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run")

[64bit nVidia 185.18.36 Download]("ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.36/NVIDIA-Linux-x86_64-185.18.36-pkg2.run")

Then for installing follow the directions found [here]("https://help.ubuntu.com/community/NvidiaManual")

Have any questions/issues feel free to let me know,
~Jeff
hey thanks bud, my display now works as it should :)

one thing though, every time i strart up or reboot my display goes back to 800x600. any way i can fix this?

---

