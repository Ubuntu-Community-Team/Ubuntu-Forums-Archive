---
title: "NVidia drivers on 7.04"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by adammouse on 2007-04-21
I'm having major problems trying to install the nvidia drivers for feisty.

I've tried numerous versions of drivers from nvidia.com , I've tried some other methods and none seem to properly work. I can get the NVidia splash screen to come up just before my X server starts but then nothing that uses opengl works. 
```
adam@grolsch:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
```
spec:
using Ubuntu 7.04, i386 architecture
amd 4600+
NVidia Geforce 7600GT graphics
Asus mainboard.

please help!

---

### Post by Derspankster on 2007-04-21
Wish I could help. Having the same issues though. Ubuntu once again is a complete nightmare when trying to set up glx/Nvidia drivers for newer cards. I'm about ready to say the hell with it - doesn't seem to be worth it.

---

### Post by ceil420 on 2007-04-21
I'm getting the "extension "GLX" missing on display" error as well, on a GeForce FX 5200 (not exactly new, but not legacy), when I try to run a game. Specifically:

```
ceil@DivineStoner:~/ut$ bash ut
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Signal: SIGIOT [iot trap]
Aborting.
```

Also, in System > Restricted Drivers, "NVIDIA accelerated graphics driver" is the only thing there. The checkbox under "Enabled" is checked, but under "Status" it says 'Not in use'. I don't know if this matters, just sayin'.

Edit: I get the same message, verbatim, as the OP when I try that command (s)he used.

---

### Post by peebly on 2007-04-21
Have you tried using envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Derspankster on 2007-04-21
Yeah, I tried Envy in Edgy. Sure fire way to break X. In Edgy, I ended up manually installing 9755 for my Nvidia 6200. Now, with Feisty, something else is very wrong here. I can't believe they even brought this release out with these kinds of issues. Pathetic.

---

### Post by ceil420 on 2007-04-21
> **peebly said:**
> Have you tried using envy.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
What is 'fakeroot', and why does Envy need it? That's an awfully fishy name for a package :x

Pardon my noobishness if it's nothing major, but that sounds like something to let me edit / without a pass, and I kinda like my security.

> **Derspankster said:**
> Yeah, I tried Envy in Edgy. Sure fire way to break X. In Edgy, I ended up manually installing 9755 for my Nvidia 6200. Now, with Feisty, something else is very wrong here. I can't believe they even brought this release out with these kinds of issues. Pathetic.

I thought it was known that nvidia wasn't very cooperative with open source OS's... I blame the hardware, not the software.

---

### Post by shane634 on 2007-04-21
Well just my two cents. Envy worked great for me. I also have the FX5200 card, and I get 1700+fps and run Enemy Territory with no problems. I am using Fiesty and the newest version of Envy. Good luck.

---

### Post by nevertrustpeas on 2007-04-21
up until now i have been using fedora only since breaking free of windows, the drivers from nvidia gave better results under fedora than windows, and to my knowledge, nvidia are renowned for having better linux drivers than windows.

however, trying to get them to work with ubuntu is proving to be aload of balls, even the lower grade non vendor drivers (which are advertised as the best option???) are a real pain. some load of headache about mismatched kmod packages and alot of xserver crashes. although this is likely to do with my sli setup


Going from my experience from fedora the ubuntu o/s is clearly the problem (or lack of experience  using ut)  i have no doubt that with the correct know how nvidia can be set up just as good as i have always had it, it is a damn hard job finding the info on in though.

Are there no Nvidia how to's??

---

### Post by Calash on 2007-04-21
Odd, on my 2 main systems Feisty picked up my nVidia cards fine.  I have to go into the restricted driver manager and enable it but OpenGL is working good on both of them

---

### Post by reclusivemonkey on 2007-04-21
> **ceil420 said:**
> I'm getting the "extension "GLX" missing on display" error as well, on a GeForce FX 5200 (not exactly new, but not legacy), when I try to run a game. Specifically:

```
ceil@DivineStoner:~/ut$ bash ut
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Signal: SIGIOT [iot trap]
Aborting.
```

Also, in System > Restricted Drivers, "NVIDIA accelerated graphics driver" is the only thing there. The checkbox under "Enabled" is checked, but under "Status" it says 'Not in use'. I don't know if this matters, just sayin'.

Edit: I get the same message, verbatim, as the OP when I try that command (s)he used.

Do you have the Nvidia driver enabled in xorg.conf?

```

grep "Driver" /etc/X11/xorg.conf

```

---

### Post by ceil420 on 2007-04-22
> **reclusivemonkey said:**
> Do you have the Nvidia driver enabled in xorg.conf?

```

grep "Driver" /etc/X11/xorg.conf

```
Yes, it says "nvidia", not "nv". And I have the "nvidia-glx" restricted package:

```
ceil@DivineStoner:~$ apt-cache policy nvidia-glx
nvidia-glx:
  Installed: 1:1.0.9631+2.6.20.5-15.20
  Candidate: 1:1.0.9631+2.6.20.5-15.20
  Version table:
 *** 1:1.0.9631+2.6.20.5-15.20 0
        500 http://us.archive.ubuntu.com feisty/restricted Packages
        100 /var/lib/dpkg/status
```

Attached is a screenshot of the "Restriced Drivers" screen. Am I doing something wrong?

---

### Post by adammouse on 2007-04-22
My NVidia accelerated graphics driver, under restricted drivers says its "in use".

I thought it would be pretty straight forward to install nvidia drivers properly on 7.04-i386. :(

I tried using the NVidia installer, but that says it can't find drivers, then its unable to compile a driver kernel :(

---

### Post by ceil420 on 2007-04-24
Envy is an evil, demonic, HELL-SPAWN that I wouldn't recommend to my worst linuxian enemy. I've just spent all morning in a CLI, and that is not something you want to wake up and deal with. Because Envy ****** something up. I'm back in a GUI (obviously, as I don't do text-based web), but that took me editing xorg.conf to use "nv" instead of "nvidia". Envy, as far as I'm concerned, is the root of all nvidia evil. Worst program I've tried in linux.

Anyway, someone tells me that I can just edit /etc/default/linux-restricted-modules-common to read DISABLED_MODULES="nv", and to edit xorg.conf to read "nvidia" instead of "nv". I haven't tried it yet, as I'm still recovering from the trauma that was my experience recovering from the royal driver-rape that was Envy, but I'll try it later.

---

