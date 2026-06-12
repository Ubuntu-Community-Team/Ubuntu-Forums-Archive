---
title: "PRIME not using nouveau on Thinkpad T530 (Optimus)"
date: 2012-10-23
forum: Multimedia Software
---

### Post by sprungfeld33 on 2012-10-23
Hi,

I am using a brand new installation of 12.10 on a Thinkpad T530 with an Nvidia Optimus graphics card. I installed only a few applications, so the installation can be considered "out of the box".

I checked whether PRIME was really using the nvidia card, but that does not seem to be the case. The nouveau drivers package is installed, but ```
DRI_PRIME=1 glxinfo | grep OpenGL
``` returns ```
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile x86/MMX/SSE2
OpenGL version string: 3.0 Mesa 9.0
OpenGL shading language version string: 1.30
OpenGL extensions:

```

So I am guessing it still uses the Intel-Card. What am I doing wrong? Do I have to "tell" PRIME somewhere to use the noveau-driver? I used 12.04 with bumblebee before, and everything was working smoothly using the optirun command.

---

### Post by Ertage on 2012-11-28
I am facing the same issue. Any news on this?

---

### Post by Yellow Pasque on 2012-11-29
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by Ertage on 2012-11-29
> **Temüjin said:**
> [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I have used bumblebee on 12.04 already, but according to the wiki, PRIME will increase the performance, so i wanted to try it out.

---

### Post by Yellow Pasque on 2012-11-29
Please link to the wiki. I'm not sure what "PRIME" is. If it's a program (and you're running bumblebee), then you would prefix the command with optirun to run it on the nvidia processor:
```
optirun <command to launch PRIME>
```

---

### Post by Ertage on 2012-11-30
> **Temüjin said:**
> Please link to the wiki. I'm not sure what "PRIME" is. If it's a program (and you're running bumblebee), then you would prefix the command with optirun to run it on the nvidia processor:
```
optirun <command to launch PRIME>
```

I found it only on [http://wiki.ubuntuusers.de/Hybrid-Grafikkarten/Prime]("http://wiki.ubuntuusers.de/Hybrid-Grafikkarten/Prime?redirect=no")

Since 12.10 it is part of the Kernel, the wiki also tells you that you have to uninstall bumblebee if you want to use PRIME. I have a fresh install, so no bumblebee installed.

---

