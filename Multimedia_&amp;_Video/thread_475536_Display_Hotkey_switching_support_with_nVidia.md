---
title: "Display Hotkey switching support with nVidia"
date: 2007-06-16
forum: Multimedia &amp; Video
---

### Post by KjetilK on 2007-06-16
I'm trying to configure my system to use the hotkey (Fn+F3 in my case) to switch between the laptop LCD monitor and an external VGA. Usually, this has worked out of the box for me, but not now.

I have read nVidias documentation at 
[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-i.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-i.html)
and it makes it clear that the conventional way of using TwinView is not what I want, it says that TwinView and hotkey switching are mutually exclusive options.

I have configured my X using nvidia-xconfig as suggested by the documentation there, and the display works fine. Interestingly, there is also a 

```

Section "Screen"
    Identifier     "External VGA"
    Device         "nVidia Corporation G70 [GeForce Go 7600]"

```

section, that contains all the right modes, but nowhere in the config is this screen referenced. I would think it would need to be in the server layout somewhere, and the hotkey would switch between the LCD display config and the External VGA config when I hit Fn+F3. 

But how this is done is not documented anywhere I've seen.

I think the  Fn+F3 is itself configured right, if I connect an external display, I can get a picture on it when I restart X and when I hit the key, it appears to try to switch modes. It just doesn't switch between the LCD display and the external display.

Any ideas?

---

### Post by abish on 2007-09-20
i cant use a external display (which i could when i was using windows!)
the Fn+F4 doesnt work!:( what changes do i need to make..?
i am using HP compaq 3425 AU model with NVIDIA.
please help me out.. because i have to connect my laptop to projectors too..

---

