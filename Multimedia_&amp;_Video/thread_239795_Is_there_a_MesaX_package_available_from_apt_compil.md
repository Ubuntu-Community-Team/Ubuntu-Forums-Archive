---
title: "Is there a Mesa/X package available from apt compiled without DRI?"
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by brkamikaze on 2006-08-19
I am a user of a SiS 741GX video card and I noticed on a LFS system that when I explicitly "forbid" Mesa and X to compile without DRI, all the OpenGL demos run faster than with the (unsupported) DRI support. For example, when I used Fedora, glxgears printed 200fps+ on the console but on the screen it looked more like 0.5 fps. Now, on the LFS system, it runs smoothly, at 300fps+ printed on the console.

I'd like to know if there is a option or a package for me to install X server and Mesa without DRI; or if there is a configuration that achieves this same thing. I am using the vanilla "X -configure" file modified only to use the resolution I want and the keyboard layout I own.

If I need to compile the package myself, I'd like to know how to integrate with dpkg and to make apt only upgrade it if it is explicitly listed. I'd also like to know how to pass my cool CFLAGS to the deb build system :)

Notice: I compiled everything with a kinda "absurd" CFLAGS, but it worked: "-O3 -pipe -fomit-frame-pointer -march=athlon-xp -mtune=athlon-xp -mmmx -m3dnow -msse"

---

### Post by brkamikaze on 2006-08-19
Tried to do a "benchmark" (if glxgears is such a thing) on the Desktop CD. Runs terribly, and doesn't print those fps lines.

---

### Post by Ziox on 2006-08-19
> **brkamikaze said:**
> Tried to do a "benchmark" (if glxgears is such a thing) on the Desktop CD. Runs terribly, and doesn't print those fps lines.

here's the command to show fps: glxgears -printfps

and also, have you tried stopping DRI from loading by removing DRI from the xorg.conf file?

---

### Post by brkamikaze on 2006-08-19
Tried that (Commented the 'Load "dri"' lines and the last three lines that configure DRI), still choppy. The FPS printed are around 150/200, slower thant the pure software compilation and the display is awful.

I explicitly compiled Mesa without DRI, by using "linux_x86-32" as the make target instead of "linux_dri". Xorg-server too, by passing "--disable-dri" to configure.

---

### Post by brkamikaze on 2006-08-19
I installed "libgl1-mesa-swrast" via Adept and it seems to work. I just wanted to know beforehand (I posted this before burning the disk) and I forgot the filesystem was writable :P

---

