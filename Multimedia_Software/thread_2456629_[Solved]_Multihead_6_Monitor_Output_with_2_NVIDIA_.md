---
title: "[Solved] Multihead 6 Monitor Output with 2 NVIDIA GPUs"
date: 2021-01-15
forum: Multimedia Software
---

### Post by ryandekker on 2021-01-15
Hi there, and thanks for reading. This is my first post (edit: in a long time), so hopefully I did it right.


I had this cool idea to upgrade from 4 monitors to 6 over the Xmas break and I still don't really have it working. Without giving you my whole life story, I'll try to include what I've tried so far. :) I'm not a total n00b but this has got me stumped and I don't know where to look for more info on what's failing to try to fix that.



First some basic info:

[LIST]
[*]Running Ubuntu 20.04.1 LTS
[*]I installed Xubuntu with [FONT=courier new]apt install xubuntu-desktop[/FONT], running on LightDM. I was on Gnome, but read that Gnome (and GDM specifically) had issues with multiple GPUs. I'm fairly indifferent on DE/DM, though so far I am liking Xfce.
[*]See output from: [lspci -vv]("https://pastebin.com/RKNcYYSb"), [xrandr -q]("https://pastebin.com/tTz7YYLf"), [Xorg.0.log]("https://pastebin.com/zq3DaAhF")
[*]2 NVIDIA GPUs: GeForce GTX 1060 6GB (primary, GPU-0) and Quadro P1000 (GPU-1)
[*]I have 6 monitors total, 4 plugged into GeForce, 2 into Quadro
[*] Using nvidia-driver-460
[/LIST]

I DID get 6 monitor output using Xinerama thru my xorg.conf (with nvidia-settings), but it was flashy and generally awkward. Buggy enough that I prefer going back to 4 monitors for the time being.

I figured that switching off Xinerama to simply RANDR would be a win, but [FONT=courier new]xrandr --auto[/FONT] only shows displays from one GPU at a time (either/or, but not both simultaneously). I created an xrandr snippet using ARandR, but that [gets hung up]("https://pastebin.com/C5CV1AyH") at the first display on the second GPU. The most stable config here is running without an xorg.conf file and just letting things fall into place, but still only 1 GPU will output at a time. This (and it working with Xinerama) seems to indicate that this is configuration related not hardware or actual driver support, etc. Despite the fact that there is no xorg.conf file, there's a ton of stuff in /etc/X11/Xsession.d/. Maybe something in there is conflicting some how? I kinda looked through it and nothing jumped out at me.

I found [this post]("https://collaboradev.com/2016/09/30/arch-linux-hydra-build/") where the guy got both 2 Xscreens working using his xorg.conf file without Xinerama, and all 8 monitors on the same Xscreen using BaseMosaic (which I thought was capped at 3). But it's a bit older and seemed to be dependent on an older nvidia-driver (than he was using, 367 vs 370; much older than mine at 460). Plus he installed directly from the NVIDIA site, and I've had better luck with the NVIDIA drivers installable via apt from the main Ubuntu repos. I thought about downgrading to try that old version but recent versions gotta have decent support too, right?

I also started working through this [Multiseat wiki page]("https://help.ubuntu.com/community/MultiseatX#LightDM"), and that may yet be a solid bet, but there's a lot there and mostly centered around real multiseat (i.e. multiple sets of input devices for multiple users) and not multiple Screens for the same user. It seems like also those Screens wouldn't allow interaction between the two so even if I got it working would be less than ideal (though better than both Xinerama and only 4 monitors).

Couple other tidbits:
```
$ xrandr -v
xrandr program version       1.5.0
Server reports RandR version 1.6


$ xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x1b8 cap: 0x1, Source Output crtcs: 4 outputs: 9 associated providers: 1 name:NVIDIA-0
Provider 1: id: 0x3c5 cap: 0x2, Sink Output crtcs: 4 outputs: 8 associated providers: 1 name:NVIDIA-G0

```

Let me know what other info would be helpful and I can post it here.

Any help would be greatly appreciated! Thanks in advance!

---

### Post by ryandekker on 2021-01-22
Good news, I was able to solve this with some points from the guy who wrote the blog I referenced in my post. Starting here: [https://collaboradev.com/2016/09/30/arch-linux-hydra-build/#comment-137815](https://collaboradev.com/2016/09/30/arch-linux-hydra-build/#comment-137815)

Bottom line: Nvidia's Mosaic tools require identical GPUs in order to work (see: [https://nvidia.custhelp.com/app/answers/detail/a_id/3580/~/how-to-configure-mosaic-on-linux](https://nvidia.custhelp.com/app/answers/detail/a_id/3580/~/how-to-configure-mosaic-on-linux)). Once I got that and was able to set it up with nvidia-settings (set up, restart X, set up again), then everything worked naturally, including with ARandR and display pane in Xfce.

Hopefully this helps someone!

---

