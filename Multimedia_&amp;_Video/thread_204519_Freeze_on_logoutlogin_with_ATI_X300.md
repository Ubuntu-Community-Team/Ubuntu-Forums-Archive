---
title: "Freeze on logout/login with ATI X300"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by fraforno on 2006-06-27
Hello everybody,

I switched to Kubuntu a few weeks ago and I will never be going back, but I'm experiencing some video card problem with Kubuntu Dapper Drake.

I installed the latest video drivers from the ATI web site, used aticonfig to modify my xorg.conf and everything seems to be fine, however I still have some random freezes when loggin out; more precisely:

1) Logging out and then loggin in again with the same user almost always produces a freeze

2) Turning off the computer sometimes produces a black screen freeze

I was wondering if anyone of you experienced similar problem and what could I try to solve them (system logs didn't prove useful). My video card is an ATI Radeon X300.

Thank you.

---

### Post by andrex on 2006-07-01
Hi,
i have the same problem.
I have an (or more correct) two ati radeon x1600Pro 128Mb graphic cards.
I have installed fglrx driver (8.26.18-x86_64) downloaded from ATI.
I have build the driver package for ubuntu and the kernel module, and all seem to be   OK.
I have configured xorg 7.0 with aticonfig --initial=dual-head.
Sometime, when i start X all go fine, but, more times, the Xorg (and sometime all system) freeze.

Somebody has any idea ?

Tahnks
Andrex

---

### Post by Orion Mayair on 2006-07-01
Hi andrex,

You might want to try the 8.25.18-x86_64 ATI Driver...

I was running the 8.25.18-x86 ATI Driver with Good Performance & Speed...
When I installed the 8.26.18-x86 ATI Driver... My System Locked Up and now it won't boot into Graphics Mode.

---

### Post by jkwarras on 2006-07-05
I have the sma eproblem with an ATI X700, and apparently it's casued by the ATI drivers, that crash the X server when login out or shutdown the system. Just to see that it's a fglrx driver issue, try to change the xorg.conf to "radeon" or "vesa" and you'll probably be able to shutdown or login out without crashes.

---

### Post by jkwarras on 2006-07-06
For those having problems with their X server freezing the PC (black screen, no response), there's a way to make the system work normally, but it depends a lot on your system, so it's a "try & pray" solution :)

That's what I've done:

- Edit /etc/gdm/gdm.conf as root and uncomment and change this line to:
```
AlwaysRestartServer=true
```
([http://www.thinkwiki.org/wiki/Problems_with_fglrx#Hardlock_on_X_logout](http://www.thinkwiki.org/wiki/Problems_with_fglrx#Hardlock_on_X_logout))

- Edit /etc/X11/xorg.conf as root and comment/remove Option "DPMS" if it's there.
([http://ati.cchtml.com/show_bug.cgi?id=239#c48](http://ati.cchtml.com/show_bug.cgi?id=239#c48))

- Change the monitor plugin from DVI to D-Sub.
([http://ati.cchtml.com/show_bug.cgi?id=239#c48](http://ati.cchtml.com/show_bug.cgi?id=239#c48))

In my particular case, only the third option finally solved my problems but I've left the two other changes there in case...

Hope it helps and now you can logout, shutdown, etc... correctly

---

### Post by DoubtingThomas on 2006-07-06
Same issues with my Mobility 9700 card.  I get the login screen just fine, but then gnome never loads.  Howerver, I took a different approach to getting mine to work, I commented out the 'load "dri"' but left the driver as "fglrx" soooo, I have no 3D support but I can login :-? 

I have spent the last 3 days trying to get 3D rendering to work (I have followed every fglrx variant in this forum and scratch-reinstalled many times).   Just starting to get a bit frustrated.](*,) 

@jkwarras:

I will give your suggestions a whirl tonight *crosses fingers*

---

### Post by pungliist on 2006-07-06
Same problem here with a 9600/9700 Mobility on a vaio laptop... It was working few month ago :'(.
The only solution to get fglrx working is deactivating the DRI support. I tryed latest ati drivers and latest kernel (2.6.17) built manually.
the system freeze after DRI loading...

Please help us ! :)

---

### Post by DoubtingThomas on 2006-07-06
@pungliist:

Good (well not really;) ).  At least there seems to be a pattern emering with the fglrx driver and DRI.  

I would urge everyone to try the same thing (leave *driver "fglrx"* and comment out *load "DRI"*) and verify you can load into GNOME.

---

### Post by jkwarras on 2006-07-07
Apparently the freeze on logout/shutdown is caused by a problem with ATI driver and the DVI. I just had to swith the plug and everything works now.

I have DRI enabled and have 3D support. According to this post:
[http://ubuntuforums.org/showthread.php?t=197471&highlight=fix+fglrx](http://ubuntuforums.org/showthread.php?t=197471&highlight=fix+fglrx)

you have to add this lines to /etc/modules
```
agpgart
fglrx
dri
```

It works for me. Hope it helps.

---

### Post by pungliist on 2006-07-07
Thanks but i have a laptop :( So i can switch to VGA... It must be the same pb but i need to get it working cause i can't bring my 22" CRT monitor with me :-?

---

### Post by pungliist on 2006-07-10
No reply ... :'( Is there any bug logged about this pb ?

---

### Post by sYs^ on 2006-07-12
My PC crashes (no response, monitor turns off) everytime when I want to shut it down.
I use the DVI output on my X800GT and the fgrlx drivers.

Any ideas?

---

