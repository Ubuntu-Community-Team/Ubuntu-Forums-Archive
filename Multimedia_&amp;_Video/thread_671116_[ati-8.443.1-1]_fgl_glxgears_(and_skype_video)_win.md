---
title: "[ati-8.443.1-1] fgl_glxgears (and skype video) window not showing content"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by MadeR on 2008-01-18
I have just installed the 8.443.1-1 drivers for ATI (X1650) using the Dells Dynamic Kernel Module Support Framework.

Before upgrading to this version, I was simply using the propietary drivers in my kubuntu gutsy, enabled by the KDE control center.

I unchecked the flag and rebooted.

Vesa mode

After installing the new drivers with dkms method (and package as well), I removed fglrx and added the modes "1280x1024" to xorg.conf.

When I start and fgl_glxgears window (or when I use skype with webcam, video window enabled), I can see the borders of the window, but not the content: instead what was below the window, when the window was created, is shown.
If another application covers the window, it "stains" the window, and the content of the application remains over the window.

The applications (fgl_glxgears and skype) work, and do not crash.
In skype I can still hear the sound and the partner can see me.
fgl_glxgears still writes the benchmarks on the konsole window.

can anyone help me?

you can see an image of what is happening and the content of the main configurations files here: 
[http://forum.skype.com/index.php?s=&showtopic=106485&view=findpost&p=486989](http://forum.skype.com/index.php?s=&showtopic=106485&view=findpost&p=486989)

---

### Post by MadeR on 2008-01-21
in the skype forum they suggested to add ```
Option      "TexturedVideo"         "on"
``` to xorg.conf, but nothing changed :(

---

### Post by MadeR on 2008-01-21
> **MadeR said:**
> in the skype forum they suggested to add ```
Option      "TexturedVideo"         "on"
``` to xorg.conf, but nothing changed :(
I tried activating opengl overlay or xv overlay, but nothing changed.
I tried with or without the TexturedVideo option...
I tried also commenting all the options in the device section of fglrx device.

Any guess? :(


(taking note: next time buy an nvidia card and never again ati)

---

