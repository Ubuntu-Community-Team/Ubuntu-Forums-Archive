---
title: "Video stuttering forever &lt;3"
date: 2011-12-19
forum: Multimedia Software
---

### Post by alfhakon on 2011-12-19
Hello, I've been an ubuntu user for some years.
I bought a new laptop for this semester, a samsung RC530 (and I'm using bumblebee to get optimus working correctly), and I'm very happy with it. I installed ubuntu 11.10 on it, and naive as I was, I thought that my previous problems with this operating system would magically disappear =/

I love linux and open-source stuff, BUT there's one thing that's always been like sand in my ***: video stuttering.

As long as I've been using ubuntu I've been having this problem. I guess it's relevant to mention that all thee computers I've used has an Intel processor and nVidia graphics card, including this one.
The video tearing occurs in both VLC and mplayer, and I have no idea what is wrong. I've been googling and searching these forums for solutions to this thousands of times, but I never seem to find it.

So now I'm creating my own post. Thanks in advance :)

---

### Post by alfhakon on 2011-12-20
I'm sorry, but I need to bump this

---

### Post by alfhakon on 2011-12-23
Are there no ideas of how to fix this? I tried switching to openSUSE now, but the tearing is not gone. Although, bumblebee didnt install correctly because of some wierd reason.. 

Anyways, it seems that I've only been having this problem in Linux operating systems. Windows seems to work fine, but oh dear god, I dont want to go back:(:confused:
It may be a problem with the nvidia drivers? cuz I've only been having nvidia in my entire pc history

---

### Post by alfhakon on 2011-12-25
I actually found a solution to my years of suffering, over at the arch linux forums :D
Here it is!


1) Make sure vsync is enabled on your driver's options


2) Edit /etc/enviroment and add the lines:

CLUTTER_PAINT=disable-clipped-redraws:disable-culling CLUTTER_VBLANK=True
3) Reboot


Worked like a charm. No tearing whatsoever! 

Source: [https://bbs.archlinux.org/viewtopic.php?pid=1017705#p1017705](https://bbs.archlinux.org/viewtopic.php?pid=1017705#p1017705)

---

