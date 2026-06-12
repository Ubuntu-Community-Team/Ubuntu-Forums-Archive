---
title: "nvidia drivers not working with geforce9600 on new hardy install"
date: 2008-10-27
forum: Multimedia Software
---

### Post by doesntcount on 2008-10-27
As a very new user of ubuntu (coming from gentoo) I need some help configuring my new hardy installation to use nvidia drivers. I'm slightly disappointed in the difficulty I've had with this, considering I spent much less time configuring gentoo (a much more demanding os in terms of things not working out of the box and requiring manual interventions).

My hardware is a Nvidia Geforce 9600 gt.

I first tried following this howto ([http://www.funnestra.org/ubuntu/hardy/](http://www.funnestra.org/ubuntu/hardy/)) but i was given this error:
```
VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.
```

I abondoned this howto and went with this one [http://ubuntuforums.org/showthread.php?t=880787&highlight=nvidia+installation+problems+hardy](http://ubuntuforums.org/showthread.php?t=880787&highlight=nvidia+installation+problems+hardy).

The EnvyNG program didn't recognise my card as compatible with driver (I didn't the 9600 was that uncommon???). So I did the "Tricky" installation.

Followed the instructions, ran nvidia's installer, ownloaded the drivers from nvidia's website, but when i started gdm back up, the screen flashed a few times and put me at 800x600. nvidia-settings tells me i'm not using the nvidia x driver. Dropping out of x and running nvidia-config doesn't help.

I have yet to do the "Tricky Tricky" way, but I'm hoping someone will have some words of wisdom before I tackle that.

Thanks in advance for help!

---

### Post by doesntcount on 2008-10-27
Didn't know this was an option with envyng, but i went to it's gui application and told it to manually install the latest nvidia drivers. It did a whole bunch of work (much more than the nvidia installer did) but it successfully installed it, and I'm all set. So that's a relief.

Now, a quick follow up question: in gentoo, everytime you recompile the kernel, you have to reemerge the nvidia-drivers package. Is there a similar requirement for ubuntu?

Thanks.

---

### Post by doesntcount on 2008-10-27
* Update - Changed subject title *

So even though envy successfully installed the nvidia driver, I don't have glx support:

```
$ glxinfo
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

Here's what X has to say about this:

```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
dlopen: /usr/lib/xorg/modules/extensions//libglx.so: undefined symbol: _nv001464gl
(EE) Failed to load /usr/lib/xorg/modules/extensions//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)
(II) LoadModule: "int10"
```

The nvidia drivers I have installed are 173.14.12, which look to be what I want, according to other posts.

Also, I've tried installing both nvidia-glx and nvidia-glx-new, neither works. In fact, when I install either of them, they screw over the nvidia driver and I have to reinstall it using envy. THis is all very annoying especially with hardware that's been around long enough and a linux distro that's been out for months :(

Please help. Thanks.

---

### Post by norwoods on 2008-10-31
i think you need nvidia driver 177.80 for the 9600gt.

---

