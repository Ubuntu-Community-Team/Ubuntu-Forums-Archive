---
title: "Beryl/fglrx w/ ATi Radeon X600 won't work"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by Tank90 on 2007-02-05
Hello folks,

I just re-installed Ubuntu (problems with GRUB) and I'm trying to install Beryl which I ran on my old installation. Unfortunately, I'm the unfortunate owner of a ATi graphics card. This is the output I get when i run fglrxinfo:

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

Now, it should work, shouldn't it?

I then did this:
```

sudo aptitude install beryl emerald-themes

```

Beryl and Emerald installed fine and I decided to try my luck by typing beryl in the terminal. Beryl then writes the following:

```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing

```

And now I'm completely lost. I've looked in my xorg.conf file and the DRI module is loaded and I have a DRI section, so it is loaded :/ And then I noticed something strange:

```

Output from fglrxinfo: display: :0.0  screen: 0
Output from beryl: Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".

```

I don't know what this means, so I'm pretty lost right now. While we're at it, what the ... is two texture support?

Hope you can help me to get this up n' running. Ubuntu and Beryl absolutely rocks :)

Thanks in advance,

Dan

---

### Post by divague on 2007-02-05
Hi, i had that problem too, since i couldn't find a solution, i just downgraded beryl to its previous version. I'm guessing you installed version 0.1.9999.1
Open synaptic package manager, search for beryl, press ctrl+e and select version 0.1.99.2
you have to do this for beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-binding, libberyldecoration0 and libberylsettings0

hope this helps you.

---

### Post by fitzman49 on 2007-02-05
> **Tank90 said:**
> Hello folks,

I just re-installed Ubuntu (problems with GRUB) and I'm trying to install Beryl which I ran on my old installation. Unfortunately, I'm the unfortunate owner of a ATi graphics card. This is the output I get when i run fglrxinfo:

```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X600 Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

Now, it should work, shouldn't it?

I then did this:
```

sudo aptitude install beryl emerald-themes

```

Beryl and Emerald installed fine and I decided to try my luck by typing beryl in the terminal. Beryl then writes the following:

```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display localhost:1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing

```

And now I'm completely lost. I've looked in my xorg.conf file and the DRI module is loaded and I have a DRI section, so it is loaded :/ And then I noticed something strange:

```

Output from fglrxinfo: display: :0.0  screen: 0
Output from beryl: Xlib:  extension "XFree86-DRI" missing on display "localhost:1.0".

```

I don't know what this means, so I'm pretty lost right now. While we're at it, what the ... is two texture support?

Hope you can help me to get this up n' running. Ubuntu and Beryl absolutely rocks :)

Thanks in advance,

Dan

Try typing ```
beryl-xgl
``` instead of ```
beryl
```.  I had the same problem with my card even with the dri not displaying on display 1.0 and just changing the boot command fixed it.:)

---

### Post by Tank90 on 2007-02-05
> **divague said:**
> Hi, i had that problem too, since i couldn't find a solution, i just downgraded beryl to its previous version. I'm guessing you installed version 0.1.9999.1
Open synaptic package manager, search for beryl, press ctrl+e and select version 0.1.99.2
you have to do this for beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-binding, libberyldecoration0 and libberylsettings0

hope this helps you.

This worked just perfect, fantastic! :) Really can't thank you enough, but thank you!

Just a small comment: I tried with the beryl-xgl command first, but that didn't work at all, thanks though :)

- Dan

---

### Post by ProjectWhat on 2007-03-30
ctrl+e doesnot work in synaptic.. Is there an alternative?

---

### Post by jcronkhite on 2007-04-01
For others that might stumble upon this thread, here is a link that worked perfectly for my ATI x600 in an HP Pavilion zd8000:

[http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html](http://koti.mbnet.fi/waappu/edgy_ati_aiglx_beryl.html)

---

