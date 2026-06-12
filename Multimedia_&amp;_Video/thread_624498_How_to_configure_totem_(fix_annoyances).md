---
title: "How to configure totem? (fix annoyances)"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by gaspard.leon on 2007-11-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/172247](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/172247) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Using totem (w xine back-end)

Two items are annoying, otherwise it seems to work well.

Anyone noticed these?

1. The controls in full-screen flicker when moving the mouse, instead of coming on and off cleanly they flicker hard, and it's irritating to get them, once they stick it's ok (move mouse slowly), and yes I've reported it as a bug.

2. The refresh rate of the video doesn't match the screen, so fast action segments of the video playback show horizontal  "tearing" (like when "Vsync" is turned off in a 3D game..)

So, my questions to all:

How can I configure Totem or Xine? can I change the "fade in and out" controls in full-screen, perhaps that would fix the flickering, can I change the refresh rate of video rendering?

My system:
Ubuntu 7.10 with compiz enabled, using emerald, using nvidia restricted drivers
Nvidia Geforce 5900XT
AthlonXP 3200+ with 2GB on Abit NF7-S (nForce 2 Ultra)
Lots of harddrives, SCSI, SATA, and IDE

cheers,

Gaspard

---

### Post by erginemr on 2007-11-27
Hello,

I am also having the tearing effect, but having this only when Compiz Fusion is enabled. So, I believe it has something to do with Compiz. I have worked around the problem by installing GXine as a backup video player, the Gnome Xine player, which has a better and simpler look and interface, and does not exhibit the tearing effect when playing video in full screen, at least in my system.

Now that you are also using NVidia, you may try the settings (esp. those related to vsync) by running "nvidia-xconfig" with Alt+F2 and looking for the settings related to video syncronization.

(P.S. You can install it with "sudo aptitude install gxine".)

---

### Post by gaspard.leon on 2007-11-27
thanks!

I'll try those things tomorrow after work

---

### Post by gaspard.leon on 2007-11-28
well gxine has similar tearing for me so I'll hunt around the nvidia driver settings.

---

### Post by gaspard.leon on 2007-11-28
ok well gxine is ok but you can't double click to fullscreen (yes you can probably change it but I don't feel like it right now)

And it didn't fix my tearing problem.

So!

I tried the command:
```
nvidia-xconfig -A
```
(advanced help command)
and reading through the options
I found one that helps!

```

 --xvmc-uses-textures
      Forces XvMC to use the 3D engine for XvMCPutSurface requests rather than
      the video overlay.
```

The option causes the following line to be added to the Section "Screen" in your xorg.conf file:
```

    Option         "XvmcUsesTextures" "True"

```

AND, more importantly; it works, it seems to have fixed my tearing problems (in totem!) I tried several fast action videos and didn't see the horizontal tearing...

anyone else?

---

### Post by gaspard.leon on 2008-04-03
further to all this porking around with the video settings, I was playing with compiz settings the other day, and noticed a setting under "General Options" > "Screen Options" > "Sync to Vblank"

Now I can have non-tearing videos under compiz too!! :popcorn::grin:

---

### Post by Fodox on 2008-04-17
I also have the "flicker" problem!
I noticed that with graphic details sets to minimal, the problem disappears. I have a NVidia graphic card, with last NVidia drivers updated.

---

