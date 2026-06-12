---
title: "strange problem with video playback"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by hvdhvd on 2006-12-14
hi 
this problem is bugging me since 2 weeks:
i have a agp ati radeon 9100 128mb graphic card chipset r200, ubuntu edgy,using "ati" driver. 
in any player mplayer,xine, totem, vlc theres only black video with sound. using the default xv output. also on any output similar to it like xvidix etc. the x11 plays fine but its pixalated and i dont like it. the opengl output is choppy and drops too much frames.
notes:
-everything other is working fine, direct rendering, 3d stuff. like beryl is ok with nearly every efect, i can run racer in 1280*1024 with more than 50fps, glxgears gives more than 1400fps.
-after few days i found out, a setting of "xvideo adapter number" from -1 to 1 in vlc, plays xvideo but only in original resolution, stretched or fullscreen is again pixalated like x11.
-tried ati fglrx drivers,the last with support of 9100, but they froze the whole system to only hard reset, randomly after cca 1min of loading the system. i gave them after few days another try, the same results, but found out, if i run the system with "single" like in recovery mode, and run vlc,mplayer from console, and the xv worked.. but that is not i have wanted it, no window manager running etc. and i would like not to use fglrx
-after a week a tried other live distros sabayon, mepis, puppy, dsl ... with the same problems
-i have a 9000 agp at my sisters computer, video works fine out of the box. a 9100 igp in barebone computer in living room, video works fine out of the box also in ubuntu. only this one is giving me headaches, i have to boot to M$ to watch xvid films, which i do a lot.
-the card seems fine, plays 720p videos fine in M$.

i run out of ideas where the problem could be. monitor,card,xorg,driver,players,codecs
any help greatly welcome and sorry for my english

---

### Post by Sinisterff on 2006-12-17
I have the same problem with VLC, it show back and just the sound. But i had beryl activated, so i did this in terminal:

```
metacity --replace
```

that replaces beryl with metacity, so it removes all the effects, but the video plays fine in metacity, anyone know why is that?

i do not know if it's the same problem you have, but perhaps?

i have an intel graphics card 945GM

---

### Post by Stanleyok on 2006-12-25
I had a very similar problem. Whenever I had video output in any player, the video would play for a second, and then the screen would go blank. I could never get fullscreen to work. I played around with the "adapter number" options under video/output modules  in VLC (thanks for the tip, hvdhvd), and after I set all of them to "1", video worked in VLC. I am very excited! However, video is still iffy in other players.

---

### Post by .k2600. on 2007-04-02
> **Stanleyok said:**
> I had a very similar problem. Whenever I had video output in any player, the video would play for a second, and then the screen would go blank. I could never get fullscreen to work. I played around with the "adapter number" options under video/output modules  in VLC (thanks for the tip, hvdhvd), and after I set all of them to "1", video worked in VLC. I am very excited! However, video is still iffy in other players.


Same here, this tip also helped on ati9800pro/aiglx/beryl

---

### Post by Dr. Nick on 2007-04-02
Switching from beryl to metacity fixes all my playback issues. If i use beryl I get blocky video in mplayer and no video in totem.

---

