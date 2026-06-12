---
title: "Huge problem installing Quake 1"
date: 2011-08-15
forum: Multimedia Software
---

### Post by jfed on 2011-08-15
Hello. As the title suggests, I am trying to install Quake 1. I do not have the original CD. A friend of mine purchased the game, and I he used his WADS to install Quake 1 on me Wii, via the homebrew channel. I only mention that because I'm not sure if the wads i have off the sd card after the installation are the same as the vanilla ones you obtain from purchasing the game, i sure hope so. I do have a copy of the id1 folder, with the pak0.pak and pak1.pak files, as well as the other files inside the id1 folder. Now I know that there are multiple posts about this on the internet already, and I've read a good deal of them, however nothing I try seems to work, so thats why I turned here. I've been trying to use tyrquake to install quake 1. And everything goes good and works so far, untill I try to run the tyrglquake binary, then the program segfaults, and my monitor's rez defaults to 480p. I have no clue what to do. Here is what my terminal reports back to me as I try and run the tyrglquake binaries.

```
justin@justin-laptop:~/Desktop/tyrquake-sa-0.54$ ./tyr-glquake 
Playing registered version.
Console initialized.
UDP Initialized
Exe: 18:27:35 Jun 25 2006
32.0 megabyte heap
Using XFree86-VidModeExtension Version 2.2
GL_VENDOR: Tungsten Graphics, Inc
GL_RENDERER: Mesa DRI Intel(R) 965GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2
GL_VERSION: 2.1 Mesa 7.9-devel
ARB multitexture extensions found.
ARB multitexture extension enabled
-> 8 texture units available
Video mode 640x480 initialized.
gl_texsort is obsolete.
gl_keeptjunctions is obsolete.
gl_reporttjunctions is obsolete.

Sound Initialization
/dev/dsp: No such file or directory
Could not open /dev/dsp
S_Startup: SNDDMA_Init failed.
Received signal 11, exiting...
Segmentation fault
justin@justin-laptop:~/Desktop/tyrquake-sa-0.54$ 

```

After running that I am able to see the quake 1 splash screen for half a second, before it crashes.

I'm not sure if any of that is helpful or not, I'm just looking for some guidance. If anyone can tell me what to do to fix this that would be great, or any other way to install Quake 1 without the CD would be great, thanks in advance.

---

### Post by .... on 2011-08-15
That kind of sounds like piracy, but for your sake, I'll assume it's not.

```
sudo apt-get install game-data-packager
```^You use that to create a quake-registered .deb of the data files for the game.  Then, you get quake and quake-server packages from Debian, install them, and frag on happily ever after. [http://packages.debian.org/search?suite=experimental&searchon=names&keywords=quake](http://packages.debian.org/search?suite=experimental&searchon=names&keywords=quake)

EDIT: Oh yeah, you probably need quakespasm package too: [http://packages.debian.org/source/sid/quakespasm](http://packages.debian.org/source/sid/quakespasm)

---

### Post by jfed on 2011-08-15
Ohhhh, I didn't think of that. And thanks, it worked like a charm.

And btw, its not piracy haha, Quake 1 is open source!

but anyway, thanks so much, helped alot.

---

