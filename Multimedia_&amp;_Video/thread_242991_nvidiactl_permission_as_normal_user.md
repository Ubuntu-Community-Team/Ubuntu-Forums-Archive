---
title: "nvidiactl permission as normal user"
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by Gutter on 2006-08-24
Ok I've been searching quite a while, and all the solutions I find are either temporary or they don't apply to Ubuntu.

When I run glxgears as a normal user I get 

```
NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
```

Of course, if I run it with "sudo glxgears" everything works.

I've tried adding myself to the video group, and although I see my user in there, it doesn't work more.  I even tried to add my normal user to the root group, and it doesn't work. (I've removed it since)

I've tried changing the permission of the file and it works, but only until my next X session. Apparently /dev/nvidiactl is created dynamicaly, and everytime it is, its with permission 660, so I need to rechange the permission manually.

I wouldn't mind really, but this means that I cannot try stuff like compiz because my permission are stuffed when I reboot, so compiz doesn't load as it can't use my video card.

I have 
-a sli setup, with 2 nVidia 6600 GT of the same brand.
-did apt-get update and apt-get dist-upgrade (this is a brand new installation, I hosed my old one trying to make that work yesterday... the X server wouldn't start anymore)
-the drivers work, I see the starting logo and glxgears run @ 7000 fps in full screen (after I change the permission of course). I don't know if it uses both video cards but anyway...

Anyone knows how I could make the permission stick? I found the nvidia-kernel file, who seems to set the permission, but something tells me I shouldn't change that file.

(and yes, I'm a utter newbie)

---

