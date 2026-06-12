---
title: "Ubuntu 10.04 with 3.x kernel - broken openGL?"
date: 2013-10-15
forum: Multimedia Software
---

### Post by Stanislav_Nekrasov on 2013-10-15
Hello!

I'm trying to install a specific software which depends on using Ubuntu 10.04. For the reference - [http://wiki.xibo.org.uk/wiki/Install_Guide_Python_Client#Ubuntu_10.04_and_derivatives](http://wiki.xibo.org.uk/wiki/Install_Guide_Python_Client#Ubuntu_10.04_and_derivatives)

The thing is, i have a very new hardware with on-board intel HD4000 video (Gigabyte GA-H77-DS3H).
So from the beginning i had software working perfectly but extremely slow video perfomance. Apparently video was sort of broken and didn't allow me to have more than 800x600 resolution (VESA driver?)

I have almost zero knowledge about linux video drivers/opengl workings (usually i only deal with it from command line).

So i tried to search for ideas and there were 3: use some ppas to update to more new kernel (2.6.38), use backported oneiric 3.0 and build my own 3.x kernel. 2.6.38 didn't help, but in both 3.0 and 3.8.8 kernels i get pretty good video performance in X itself and even fullhd video from youtube works nice.

BUT. Xibo software apparently relies on openGL, and i can't start it on those new kernels. The glxinfo output is:
```
glxinfo 
name of display: :0.0
Unrecognized deviceID 0x152
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  21
  Current serial number in output stream:  24


```

Please, help me  to diagnose and fix this situation (if possible) as i have no idea about how all this works and 99% of google links tell to mess with ATI proprietary-or-not drivers, and i don't have ATI, i have Intel HD4000.

Thanks.

---

### Post by Yellow Pasque on 2013-10-15
The problem is that you're looking at outdated documentation. Xibo (including python client) looks to be an actively developed project, so there should be no need to use an EOL (End of Life) release like Ubuntu Lucid/10.04

---

### Post by Stanislav_Nekrasov on 2013-10-16
It is of course active, but for python client developers don't have time to invest into adapting for other than their test systems as far as i understand. There is a thread on google groups where main dev tried to compile Berkelium under 12.04 LTS but has had no success.
Though i found out that 12.04 LTS isn't supported by intel anyway (in the light of Ivy bridge cards).

---

