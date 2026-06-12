---
title: "Broken X server not related to sticky"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by kom on 2007-01-12
Hi,
       I recently bought an Nvidia GeForce 6200 256 MB video card to replace my old Nvidia card. In order to test it out, I ran Doom 3 on Windows after installing DirectX, OpenGL etc. and it ran like a charm, the graphics looked awesome as compared to my old graphics card. Then came Linux's turn. I wanted to convince myself that Linux(Ubuntu Edgy Eft) can do just as good so I tried Doom3 on that after confugring the graphics card but it didn't run as good so probably my card wasn't configured properly. 

I therefore went to Nvidia's site and downoaded Nvidia linux drivers from: 

[http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html]("http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html")

Now in order to install I had to make sure that X wasn't running and I did everything I could to somehow start Ubuntu in console mode with X not running i.e.
CTRL+ALT+BACKSPACE
CTRL+ALT+F1
init 3
telinit 3 
single user mode
using GRUB etc.

For all the attempts above (except single user mode) I got the message that said "It appears you are running X..." So it looks like all runlevels 2-5 in Ubuntu start X up. As for single user mode, it said that things might not work if you continue. I was so fed up that I proceeded with installing the drivers in single user mode disregarding the warning and then it did stuff like compiling the kernel etc. So, no so surprisingly I ended up with a broken X server and this is where I stand now. So right now I just want to:

_*** reconfigure/reset/reinstall my X server so that it's back up and working again. **_

I tried dpkg-reconfigure xserver-xorg

but that didn't seem to work or maybe I missed a few steps while doing that.

Note that my problem is not related to the sticky on the main page where by updating the kernel breaks nvidia drivers/X because I never updated the kernel during all the episode mentioned above.

Also, once I am done getting my X server to work I would like to properly configure my Nvidia graphics card with OpenGL, Linux equivalent of DirectX if any etc. and get Doom3 to work as good as Windows, but fixing X is the first priority.

Any help is appreciated.

(I am running Ubuntu Edgy Eft on an x86 machine)

Omair

---

### Post by kom on 2007-01-12
Hi,

    Did I post this in the wrong section or is it that nobody can help me with this?

Bye

---

### Post by majoridiot on 2007-01-12
> **kom said:**
> Hi,

    Did I post this in the wrong section or is it that nobody can help me with this?

you have to allow a little time for people to see it ;)

this is how i got the nvidia driver installed on my edgy backend-

Boot into Ubuntu as normal, logging in on normal account

Open a terminal, and type:

```
sudo /etc/init.d/gdm stop
```

Press Ctrl-Alt-F1 to go from VT7 to VT1 (X uses VT7, and doesn't prompt for login)

Login in to regular account at the text login prompt

next, get a root shell and run installer:

```
sudo bash
cd <directory where downloaded driver file is located>
./NVIDIA-Linux-x86-1.0-9742-pkg1.run      (or whatever driver file you downloaded)
```

Follow the onscreen instructions from there , and you should get everything set up fine.
once it's all done...

```
/etc/init.d/gdm start
```

will restart X for you.

if you still can't get it working, you can always install the driver from the repository (not the
latest driver, but should be stable) or from the bleeding-edge repo-

[http://albertomilone.com/driver_edgy.html](http://albertomilone.com/driver_edgy.html)

---

