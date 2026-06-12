---
title: "Panels and icons not being themed"
date: 2010-08-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by getut on 2010-08-25
I have 2 test machines running Maverick and both are up to date as of this posting.

On one of the machines, the panels and icons remain at the default and aren't being themed. Firefox buttons are also the default. The window decorations are there and working and even stuff like wobbly windows and cube is working.

Can anyone tell me what is wrong with this and how to fix it?

---

### Post by MacUntu on 2010-08-25
Hm, happened to me yesterday. Running 'gnome-settings-daemon' should re-theme it.

---

### Post by getut on 2010-08-26
Thank you very much, that got it. It was still running and when I first ran it, it didn't do anything. Then I tried killing the running one then running it again and it properly themed everything.

It still isn't right though, if I log on or off or reboot, I have to do it each time I log on. Any idea how to get it to properly do it on its own at each reboot?

---

### Post by getut on 2010-08-27
Bump.. still having to do this each time but only on one of my machines.

I am aware I am using pre-beta Ubuntu, but I'm just more interested at this point in just determining if this is a problem with my machine/configuration or a known bug that is being worked on. If its a known bug, I'll happily wait for a fix. If it is a problem of MINE, then I'd sure like to know how to fix it so I can stop killing and restarting gnome-settings-daemon each time I sign off and on or restart.

BTW... It is a brand new I7 machine with an Nvidia GTX 465 video card if the hardware config may have anything to do with this.

---

### Post by MacUntu on 2010-08-27
I was using the Ambiance-Maverick-beta theme which now has become the new Ambiance theme. The theming fail happened during that upgrade and when opening the appearance properties, the selected theme was set to "Custom". Setting it to Ambiance fixed the problem.

Other than that I don't have any problems with theming.

---

### Post by getut on 2010-08-28
Hmm... I guess I'll try filing my first bug report on launchpad then. Hopefully they can walk me through getting them the info they need.

---

### Post by ranch hand on 2010-08-28
I am not sure the package to file that against but I think I would try "gnome-panel" as in, from terminal;
```

ubuntu-bug gnome-panel

```
and follow the directions.

You will need to create an account with launchpad which every one should have particularly if they are running a dev release.

All pretty easy.  There is even a page to help with selecting the correct package.

---

