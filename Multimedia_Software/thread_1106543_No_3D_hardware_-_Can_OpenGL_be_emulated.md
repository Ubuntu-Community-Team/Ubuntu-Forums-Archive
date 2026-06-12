---
title: "No 3D hardware - Can OpenGL be emulated?"
date: 2009-03-25
forum: Multimedia Software
---

### Post by LargeHadronCollider on 2009-03-25
Hello everyone,

Here is the situation:
I am running Kubuntu 8.10 inside a virtual machine using VirtualBox (on a Vista host) - hence only sort of a primitive and generic graphics card is visible to my system (instead of the GeForce that is actually in my computer).
My xorg.conf file looks therefore like this:
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```
Although there is an NVIDIA Geforce actually sitting in my computer, I cannot install nvidia-glx and configure X11 using the 'nvidia' driver, because virtual machines provide no 3D hardware support.

Now here is the problem:
I need to run a little program that kind of needs OpenGL, and makes use of the library gtkglext: If I run it, it reports of course the following error:
```
Xlib:  extension "GLX" missing on display ":0.0".

(gdis:9256): GdkGLExt-WARNING **: Window system doesn't support OpenGL.
```

So here is my question:
Is it in any way possible to software-emulate the glx-extension? The thing is that the application (gdis it's called) has really low demands and my computer is more than powerful enough to provide the OpenGL rendering through the CPU instead of 3D hardware, but the application expects GLX to be there, which I cannot provide since I cannot configure my X11 with the nvidia-glx driver.

Is there a workaround to this?

Any help would be greatly appreciated.

Thanks!

---

### Post by inobe on 2009-03-25
virtualbox uses guest additions and installs the virtual video card.


i do not know which virtual machine you are using to answer the topic title.

---

### Post by mpsii on 2009-03-25
Take a look at VMGL:

[http://www.cs.toronto.edu/~andreslc/vmgl/](http://www.cs.toronto.edu/~andreslc/vmgl/)

---

### Post by inobe on 2009-03-25
you just pulled a rabbit out of a hat, nice find :)

---

### Post by mpsii on 2009-03-25
> **inobe said:**
> you just pulled a rabbit out of a hat, nice find :)

Just us geeks... in da ha-ous -- ):P

---

