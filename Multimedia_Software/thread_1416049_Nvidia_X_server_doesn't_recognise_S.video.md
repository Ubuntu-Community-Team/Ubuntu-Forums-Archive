---
title: "Nvidia X server doesn't recognise S.video"
date: 2010-02-25
forum: Multimedia Software
---

### Post by rawbacon on 2010-02-25
Hi, I have 9.10 64 on a HP TX2020 laptop, with NVIDIA GeForce 6150. 
I can't get twin monitor to work. When I go into Nvidia X Server, it doesn't recognise the tv over s-video. According to a lot of the forums I've searched, there should be an option to enable xinerama, which there's not.
I know I should study this more and I will, but getting simple things to work takes so long on this OS and I'd really just like to see a movie.
Thanks

---

### Post by doas777 on 2010-02-25
you may need to add a few lines to the xorg.conf (or at least that used to be the way to handle that issue)

try adding these to your Screen section:
```

Option "TVStandard" "NTSC-M" 
Option "TVOutStandard" "SVIDEO"

```
note, NTSC-M is for north america. you may have to find the type that is right for your region.

---

### Post by rawbacon on 2010-02-26
Thank you, didn't help. Neither did [this]("https://help.ubuntu.com/community/NvidiaTVOut"). I guess I'll forgo tv until I can afford win7.

---

