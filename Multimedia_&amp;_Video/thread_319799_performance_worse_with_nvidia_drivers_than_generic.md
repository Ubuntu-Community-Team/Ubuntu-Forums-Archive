---
title: "performance worse with nvidia drivers than generic"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2006-12-16
Newly installed Kubuntu 64 system on a new PC (AMD 64 3400+), OK gfx card (GeForce 6200 TurboCache PCI-E) and I run **glxgears -printfps** to see what it's like. FPS of 900 is fairly lame, but for basic drivers I suppose it was to be expected. So I install nVidia drivers via Automatix and am quite amazed to find that performance has worsened still. 600 FPS now, and everything makes the system crash. Run Google Earth - crash. Try to tune in a channel with TVTime - crash. Try to play a video game - crash.

Xorg.conf and output from glxinfo are attached.

Have I done something drastically wrong or are these drivers just not usable?

---

### Post by theturtlemoves on 2006-12-16
> **pickarooney said:**
> Newly installed Kubuntu 64 system on a new PC (AMD 64 3400+), OK gfx card (GeForce 6200 TurboCache PCI-E) and I run **glxgears -printfps** to see what it's like. FPS of 900 is fairly lame, but for basic drivers I suppose it was to be expected. So I install nVidia drivers via Automatix and am quite amazed to find that performance has worsened still. 600 FPS now, and everything makes the system crash. Run Google Earth - crash. Try to tune in a channel with TVTime - crash. Try to play a video game - crash.

Xorg.conf and output from glxinfo are attached.

Have I done something drastically wrong or are these drivers just not usable?

I've never had any problems with them.

Here are two differences that I can see in my xorg.conf.
I have 
```
Section "Module"
    ...
    Load           "dbe"
EndSection
```
 
And
```

Section "Device"
    ...
    Option          "RenderAccel"           "true"
EndSection
```

Maybe these will make a difference. Try it and see.

---

### Post by pickarooney on 2006-12-17
Thanks. Tried it, but the performance is still atrocious. 
Is the fact I'm using the TV-out options linked to the terribly slow video speeds?

---

